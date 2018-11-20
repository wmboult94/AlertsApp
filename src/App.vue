<!-- Main app component -->

<template>
  <div id="app">
		<h1>FSA Food Alerts</h1>
    <AlertsList/>
  </div>
</template>

<script>
import AlertsList from './components/AlertsList'

export default {
	name: 'App',
	components: {
		AlertsList,
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #ff1a1a;
	/* font-weight: bold; */
	background: #1a1aff;
}
h1 {
	font-weight: normal;
	font-size: 50px;
	padding: 2%;
}
</style>
