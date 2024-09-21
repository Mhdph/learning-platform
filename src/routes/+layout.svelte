<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import '../app.pcss';
</script>

<div class="h-full">
	<div class="fixd inset-y-0 z-50 h-20 w-full">
		<Navbar />
	</div>
	<div class="fixed inset-y-0 z-50 hidden h-full w-56 flex-col md:flex"></div>

	<main class="h-full">
		<slot />
	</main>
</div>
