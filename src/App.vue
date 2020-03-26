<template>
	<div id="app">
		<h1>LinkedIn Killer</h1>
		<section>
			Gameplan:
			<ul>
				<li> Hitta på vilken data vi behöver ha för en användare </li>
				<li> Vilka komponenter behövs? Registrering i egen komponent</li>
				<li> Skapa template+CSS för formuläret </li>
			</ul>
		</section>
		<RegisterProfile />
	</div>
</template>

<script>
import RegisterProfile from './components/RegisterProfile';

export default {
	name: 'App',
	data: () => ({

	}),
	components: {
		RegisterProfile
	}
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
}
</style>
