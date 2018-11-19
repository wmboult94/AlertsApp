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

export default {
	name: 'AlertsList',
	components: {
		Alert
	},
	data() {

		let alerts = []
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
					clicked: false
				}

				console.log(item_obj)
				alerts.push(item_obj)
			})

			// console.log(items)
			// alerts.push(items)

		})
		// console.log(alerts)
		return { alerts }
	},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#alerts-list {
	margin: 50px;
	border-style: ridge;
	width: inherit;
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
a {
	color: #42b983;
}
</style>
