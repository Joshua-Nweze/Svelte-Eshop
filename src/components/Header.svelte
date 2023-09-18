<script>
	import { goto } from '$app/navigation';

	let searchTerm = ''

	function search() {
		console.log(searchTerm)
		goto('/search', {});
		searchTerm = ''
	}
</script>

<header class="text-gray-600 body-font">
    <div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
      <a href="/" class="flex title-font font-medium items-center mb-4 md:mb-0">
        <span class="ml-3 text-xl">Tailblocks</span>
      </a>

      <nav class="md:ml-auto md:mr-auto flex flex-wrap items-center text-base justify-center">
        <a href="/categories" class="mr-5">Categories</a>
        <a href="/cart" class="mr-5">Cart (0)</a>
      </nav>

      <div>
		<input on:keydown={(event) =>{ if(event.key === 'Enter' || event.keyCode === 13) {search()}}} bind:value={searchTerm} class="inline-flex items-center bg-gray-100 border-0 py-1 px-3 focus:outline-none hover:bg-gray-200 rounded-s-lg text-base mt-4 md:mt-0" dir="ltr" placeholder='Search products'>
	  	<button on:click={search} class="btn bg-[#FF6700] text-white p-1 rounded-s-lg" dir="rtl">Search</button>
	  </div>
    </div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
	}

	a{
		color: #FF6700;
	}

	nav {
		display: flex;
		justify-content: center;
		--background: rgba(255, 255, 255, 0.7);
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	a:hover {
		color: var(--color-theme-1);
	}
</style>
