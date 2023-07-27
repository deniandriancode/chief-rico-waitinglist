<script>
  import * as Validator from 'validatorjs';
  
  let email = "";
  let emailUnvalid = false;
  let successRegister = false;
  let items = [1, 2, 3];
  let bgIdx = items[Math.floor(Math.random() * items.length)];;
  let bgGif = `backgroundWallpaper__${bgIdx}`;

  function subscribe() {
	let data = { email: email };
	let rules = { email: 'required|email' };
	let validation = new Validator(data, rules);

	try {
	  validation.passes();
	  email = "";
	  emailUnvalid = false;
	  successRegister = true;
	} catch (e) {
	  emailUnvalid = true;
	  successRegister = false;
	}
	
  }

  function hideThisElement() {
	emailUnvalid = false;
	successRegister = false;
  }
</script>

<svelte:head>
  <title>Chief Rico</title>
</svelte:head>

<main
    class={`h-full bg-center bg-cover bg-no-repeat ${bgGif} text-white`}
  >

  <div
	class="overlay
		   absolute h-screen w-screen bg-black opacity-[75%]">
  </div>

  <section
	class="h-full px-4 md:px-32
		   relative
		   z-10
		   container mx-auto
		   w-[95%] max-w-4xl
		   flex flex-col justify-center items-center"
	>
	<h1
	  class="text-2xl md:text-4xl font-extrabold text-center py-4 my-4 px-4 border-4 border-white
			 font-['Dosis']"
	  >CHIEF RICO</h1>
	<h1
	  class="text-4xl md:text-6xl tracking-tight font-extrabold text-center"
	  >Our website is launching soon</h1>
	<p class="text-l md:text-xl text-center py-4 font-thin opacity-75">We are working hard to make an awesome website with lot of intutive features. Subscribe below to get notified when we launch and get some huge discounts as a beta tester.</p>

	{#if emailUnvalid}
	  <div class="fadeIn__animation flex items-center p-4 mb-4 text-sm text-red-600 rounded-lg bg-gray-900 opacity-[.8]"
          role="button"
		   on:click={hideThisElement}>
		<svg class="flex-shrink-0 inline w-4 h-4 mr-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
		  <path d="M10 .5a9.5 9.5 0 1 0 9.5 9.5A9.51 9.51 0 0 0 10 .5ZM9.5 4a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3ZM12 15H8a1 1 0 0 1 0-2h1v-3H8a1 1 0 0 1 0-2h2a1 1 0 0 1 1 1v4h1a1 1 0 0 1 0 2Z"/>
		</svg>
		<span class="sr-only">Info</span>
		<div>
		  <span class="font-bold">Email is not valid!</span> Please enter a valid email address.
		</div>
	  </div>
	{:else if successRegister}
	  <div class="fadeIn__animation flex items-center p-4 mb-4 text-sm text-green-400 rounded-lg bg-gray-900 opacity-[.8]"
          role="button"
		   on:click|stopPropagation={hideThisElement}>
		<svg class="flex-shrink-0 inline w-4 h-4 mr-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
		  <path d="M10 .5a9.5 9.5 0 1 0 9.5 9.5A9.51 9.51 0 0 0 10 .5ZM9.5 4a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3ZM12 15H8a1 1 0 0 1 0-2h1v-3H8a1 1 0 0 1 0-2h2a1 1 0 0 1 1 1v4h1a1 1 0 0 1 0 2Z"/>
		</svg>
		<span class="sr-only">Info</span>
		<div>
		  <span class="font-bold">Success!</span> We will let you know when the website is ready.
		</div>
	  </div>
	{/if}
	<form on:submit|preventDefault={subscribe}
		  class="w-full flex flex-col sm:flex-row gap-2">
	  <input
		class="bg-transparent focus:border-current focus:ring-transparent focus:outline-transparent
			   focus:shadow-slate-700 hover:shadow-slate-700 shadow-md
			   transition duration-700 ease-in-out 
			   flex-1"
		type="text" bind:value={email} placeholder="Enter you email"/>
	  <button
		class="my-0 py-2 sm:py-0 h-full bg-indigo-800 hover:bg-indigo-700 focus:bg-indigo-700
			   transition duration-300 ease-in-out
			   hover:shadow-slate-700 shadow-md
			   px-4"
		type="submit">Notify Me</button>
	</form>

  </section>
  
</main>

<style>
    .backgroundWallpaper__1 {
        background-image: url('/space-1.gif');
    }

    .backgroundWallpaper__2 {
        background-image: url('/space-2.gif');
    }

    .backgroundWallpaper__3 {
        background-image: url('/space-3.gif');
    }

  .fadeIn__animation {
	animation: fadeIn 500ms ease;
  }

  @keyframes fadeIn {
	from {opacity: 0;}
	to {opacity: .8;}
  }
</style>
