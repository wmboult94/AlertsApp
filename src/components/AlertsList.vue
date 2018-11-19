<!-- Component to  hold the list of alerts and search bar -->

<template>
	<div id='alerts-list'>
		<div>
			<ul>
				<li v-for='user in users'>
					<Alert/>
				</li>
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
	data () {
		return {
			users: [
				{firstname: 'Sebastian', lastname: 'Eschweiler'},
				{firstname: 'Bill', lastname: 'Smith'},
				{firstname: 'John', lastname: 'Porter'}
			],
			input_val: '',
			counter: 0,
		}
	}
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
