<script>
	import '../app.css';
	import {goto} from '$app/navigation'
	import Navbar from '../lib/Navbar.svelte';


	const goBack = ()=>{
		window.history.back()
	}
	const goForward = ()=>{
		window.history.forward()
	}
</script>


<Navbar/>
<div class="w-auto text-center flex flex-row justify-between overflow-auto m-auto bg-slate-400 p-2">
	<button class="btn btn-warning"
			on:click={goBack}>
		Go Back
	</button>
	<button class="btn btn-warning"
		on:click={goForward}>
		Go forward
	</button>
</div>



<slot />
