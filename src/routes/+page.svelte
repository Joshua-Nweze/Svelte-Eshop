<script>
  import Loader from "../components/Loader.svelte";
  import Products from "../components/Products.svelte";

  async function getProducts() {
		let req = await fetch('https://fakestoreapi.com/products')
		let data = await req.json()

		return data
  }

  let products = getProducts()
</script>

<svelte:head>
	<title>Svelte E-shop</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	{#await products}
		<Loader />
	{:then products}
		  <Products products={products}/>
	{:catch error}
		<p class="text-4xl">{error.message}</p>
		<p class="text-slate-500">Check your internet and try and again</p>
	{/await}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}
</style>
