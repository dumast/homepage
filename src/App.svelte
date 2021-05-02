<script>
	import Clock from './Components/Clocks.svelte'
	import Icons from './Components/Icons.svelte';
	import Weather from './Components/Weather.svelte';
	import * as configure from './configure.json'
	import './Colors/theme0.css';
</script>

<main>
	<h1 class="mainTitle">WELCOME, {configure.default.name.toUpperCase()} 
	</h1>
	<div class="container">
		<Clock/>
		<Icons/>
		<Weather/>
	</div>
</main>

<style>
	.mainTitle{
		font-size: 1em;
		text-align: center;
		width: 100%;
		color: var(--greetings);
	}
	.container{
		display: flex;
		flex-wrap: wrap;
		place-items: center;
		place-content: center;
	}
</style>