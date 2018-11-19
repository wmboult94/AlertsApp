<!-- Single alert component -->

<template>
	<li>
		<div id='alert'>
			<h2>{{alert.company}} - {{alert.product}}</h2>
			<div id='description'>
				<strong>Details:</strong> {{alert.title}}
			</div>
			<div id='dataset'>
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
