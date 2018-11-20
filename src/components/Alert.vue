<!-- Single alert component -->

<template>
	<li id='alert'>
		<div v-if='alert.clicked && alert.pulledExtra'>
			<h2>{{alert.company}} - {{alert.product}}</h2>
			<div>
				<p>
					<strong>Full info:</strong> {{alert.longText}}
				</p>
				<p>
					<strong>Advice:</strong> {{alert.advice}}
				</p>
				<p v-if='alert.allergens.length'>
					<strong>Allergens:</strong>
					<p v-for='allergen in alert.allergens'>
						{{allergen}}
					</p>
				</p>
			</div>
			<div>
				<strong>Date posted:</strong> {{alert.date}}
			</div>
		</div>
		<div v-else>
			<h2>{{alert.company}} - {{alert.product}}</h2>
			<div>
				<strong>Details:</strong> {{alert.title}}
			</div>
			<div>
				<strong>Date posted:</strong> {{alert.date}}
			</div>
		</div>
	</li>
</template>

<script>
export default {
	name: 'Alert',
	props: {
		alert: { // alert will hold the info about the alert
			type: Object,
			required: true
		}
	},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#alert {
	margin: 50px;
	border-style: groove;
	width: inherit;
	cursor: pointer;
	background: #e0ebeb;
	/* background: black; */
	border-radius: 25px;
	padding: 2%
}
h1, h2 {
	font-weight: bold;
	font-style: normal;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: block;
	margin: 0 10px;
	color: #4d4dff;
	font-style: italic;
}
</style>
