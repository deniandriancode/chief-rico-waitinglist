<script>
  let email = "";

  function subscribe() {
	email = "";
  }
</script>

<svelte:head>
  <title>Chief Rico</title>
</svelte:head>

<main
  class="h-full bg-top bg-cover bg-no-repeat bg-[url('/header_bg1.jpg')]
		 text-white"
  >

  <section
	class="h-full px-4 md:px-32
		   flex flex-col justify-center items-center"
	>
	<h1 class="text-2xl md:text-4xl font-bold text-center py-4 my-4 px-4 border-4 border-white">CHIEF RICO</h1>
	<h1 class="text-4xl md:text-6xl tracking-tight font-extrabold text-center">Our website is launching soon</h1>
	<p class="text-l md:text-xl text-center py-4 font-thin opacity-75">We are working hard to make an awesome website with lot of intutive features. Subscribe below to get notified when we launch and get some huge discounts as a beta tester.</p>

	<form on:submit|preventDefault={subscribe}>
	  <input class="bg-transparent focus:border-transparent focus:ring-current focus:outline-transparent
					w-54 md:w-96"
			 type="email" bind:value={email} placeholder="Enter you email"/>
	  <button class="my-4 sm:my-0 py-3 sm:py-0 sm:h-full md:w-auto px-4 bg-indigo-800 hover:bg-indigo-700 focus:bg-indigo-700"
			  type="submit">Notify Me</button>
	</form>
  </section>
  
</main>
