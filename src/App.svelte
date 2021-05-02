<script>
	import Clock from './Components/Clocks.svelte'
	import Icons from './Components/Icons.svelte';
	import Weather from './Components/Weather.svelte'
	let userName = "Terence";
</script>

<main>
	<h1 class="mainTitle">WELCOME, {userName.toUpperCase()}</h1>
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
		color: #BF616A;
	}
	.container{
		display: flex;
		flex-wrap: wrap;
		place-items: center;
		place-content: center;
	}
</style>