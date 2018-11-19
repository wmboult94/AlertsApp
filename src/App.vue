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
	color: #2c3e50;
	margin-top: 60px;
}

h1 {
	font-weight: normal;
	font-size: 50px;
}
</style>
