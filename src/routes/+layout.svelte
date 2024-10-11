<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import { Link } from 'lucide-svelte';
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
	<footer
		class="mt-3 flex w-full shrink-0 flex-col items-center gap-2 border-t px-4 py-6 sm:flex-row md:px-6"
	>
		<p class="text-xs text-gray-500 dark:text-gray-400">© 2024 LearnWise. All rights reserved.</p>
		<nav class="flex gap-4 sm:ml-auto sm:gap-6">
			<Link class="text-xs underline-offset-4 hover:underline" href="#">Terms of Service</Link>
			<Link class="text-xs underline-offset-4 hover:underline" href="#">Privacy</Link>
		</nav>
	</footer>
</div>
