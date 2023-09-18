<script>
    export let products
</script>


<!-- <section class="text-gray-600 body-font"> -->
    <div class="container px-5 md:py-24 mx-auto">
      <div class="flex flex-wrap -m-4">

        {#each products.slice(0, 8) as product (product.id)}
        <div class="lg:w-1/4 md:w-1/2 p-4 w-full">
            <a href={`/product/${product.id}`} class="block relative h-48 rounded overflow-hidden">
              <img alt={product.name} class="object-cover object-center w-full h-full block" src={product.image}>
            </a>
            <div class="mt-4">
              <h3 class="text-gray-500 text-xs tracking-widest title-font mb-1">{product.category.toUpperCase()}</h3>
              <h2 class="text-gray-200 title-font text-lg font-medium">{product.title}</h2>
              <p class="mt-1">${product.price}</p>
            </div>
          </div>
        {/each}

      </div>
    </div>
<!-- </section> -->