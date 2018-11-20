<!-- Component to  hold the list of alerts and search bar -->

<template>
	<div id='alerts-list'>
		<div>
			<ul>
				<Alert
					v-for='alert, index in alerts'
					:alert='alert'
					@click.native='clickItem(index)'/>
			</ul>
		</div>
	</div>
</template>

<script>
import Alert from './Alert'

let alerts = []
export default {
	name: 'AlertsList',
	components: {
		Alert
	},
	data() {

		fetch('https://data.food.gov.uk/food-alerts/id?_limit=10')
		.then(response => response.json())
		.then(data => {
			// console.log(data['items'])
			return data['items'].map(item => {
				// console.log(item)
				let item_obj = {
					id: item['notation'],
					title: item['shortTitle'],
					date: item['created'],
					product: item['productDetails'][0]['productName'],
					company: item['reportingBusiness']['commonName'],
					longText: '',
					advice: '',
					allergens: [],
					clicked: false,
					pulledExtra: false,
				}

				// console.log(item_obj)
				alerts.push(item_obj)
			})

		})
		// console.log(alerts)
		return { alerts }
	},
	methods: {
		clickItem(index) {
			if(!alerts[index].clicked) {
				if(!alerts[index].pulledExtra) {
					fetch(`https://data.food.gov.uk/food-alerts/id/${alerts[index].id}`)
					.then(response => response.json())
					.then(data => {
						// Take required fields, add to alerts[index] object
						// on Alert component, do v-if to check if clicked and pulledExtra
						// are true, if so, component shows extra info
						alerts[index].pulledExtra = true
						// console.log(data['items'][0])
						alerts[index].clicked = true
						alerts[index].longText = data['items'][0].description
						alerts[index].advice = data['items'][0].consumerAdvice
						alerts[index].allergens = data['items'][0].problem[0].hasOwnProperty('allergen') ? (data['items'][0].problem[0].allergen).map(allergen => {
							return allergen.label
						}) : []
					})
				}
				else { // if we've already pulled the extra info, just need to show it again
					// console.log(alerts[index])
					alerts[index].clicked = true
				}
				console.log(alerts[index])
			}
			else {
				// console.log(alerts[index])
				alerts[index].clicked = false

			}
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#alerts-list {
	margin: 2%;
	border-style: ridge;
	width: inherit;
	background: #a1a1aa;
	border-radius: 25px;
}
h1, h2 {
	font-weight: normal;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: block;
	margin: 0 10px;
	color: #42b983;
	font-style: italic;
}
</style>
