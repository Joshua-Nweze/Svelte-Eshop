<script>
    import { page } from '$app/stores';
    import Loader from '../../../components/Loader.svelte';
    import { createEventDispatcher } from 'svelte';
    
    
    let dispatcher = createEventDispatcher()
    let { id } = $page.params

    async function getProduct() {
        let req = await fetch(`https://fakestoreapi.com/products/${id}`)
        let data = await req.json()

        return data
    }

    let product = getProduct()

</script>

{#await product}
  <Loader class='flex justify-center'/>
{:then product} 
  <section class="text-gray-600 body-font overflow-hidden">
    <div class="container px-5 md:py-24 mx-auto">
      <div class="lg:w-4/5 mx-auto flex flex-wrap">
        <img alt="ecommerce" class="lg:w-1/2 w-full lg:h-auto h-64 object-cover object-center rounded" src={product.image}>
        <div class="lg:w-1/2 w-full lg:pl-10 lg:py-6 mt-6 lg:mt-0">
          <h1 class="text-gray-300 text-3xl title-font font-medium mb-1">{product.title}</h1>
          <p class="leading-relaxed">{product.description}</p>
          <div class="flex mt-6 items-center pb-5 border-b-2 border-gray-100 mb-5">
            <div class="flex ml-6 items-center">
            </div>
          </div>
          <div class="flex">
            <span class="title-font font-medium text-2xl text-gray-300">$58.00</span>
            <button on:click={() => dispatcher('addToCart', product)} class="flex ml-auto text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded">Add to cart</button>
          </div>
        </div>
      </div>
    </div>
  </section>
{/await}