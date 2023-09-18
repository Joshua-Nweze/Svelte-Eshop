<script>
	import Header from '../components/Header.svelte';
	import './styles.css';

	function a (product){
		console.log(product)
	}
</script>

<div class="app">
	<Header />
<!-- () => console.log('a') -->
	<main on:addToCart={a}>
		<slot/>
	</main>

</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		background-color: #242424;
		color: ghostwhite;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>
