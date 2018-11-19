<!-- Single alert component -->

<template>
	<div id='alert'>
		<h2>Alert Heading</h2>
		<div id='description'>
			Description: {{description}}
		</div>
		<div id='dataset'>
			Date posted: {{date}}
		</div>
	</div>
</template>

<script>
export default {
	name: 'Alert',
	data () {
		return {
			description: 'Add description',
			date: '19 November 2018',
			advice: '',
		}
	}
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
