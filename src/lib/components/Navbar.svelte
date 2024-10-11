<script>
	import { page } from '$app/stores';
	import { cn } from '$lib/utils';
	import { BookOpen } from 'lucide-svelte';

	console.log($page.url.pathname === '/about');
</script>

<header class="flex h-14 items-center px-4 lg:px-6">
	<a class="flex items-center justify-center" href="/">
		<BookOpen class="mr-2 h-6 w-6" />
		<span class="font-bold">LearnWise</span>
	</a>
	<nav class="ml-auto flex gap-4 sm:gap-6">
		<a
			class={cn(
				$page.url.pathname === '/courses' ? 'text-blue-500' : 'text-gray-900',
				'text-sm font-medium underline-offset-4 hover:underline'
			)}
			href="/courses"
		>
			Courses
		</a>
		<a
			class={cn(
				$page.url.pathname === '/pricing' ? 'text-blue-500' : 'text-gray-900',
				'text-sm font-medium underline-offset-4 hover:underline'
			)}
			href="/pricing"
		>
			Pricing
		</a>
		<a
			class={cn(
				$page.url.pathname === '/about' ? 'text-blue-500' : 'text-gray-900',
				'text-sm font-medium underline-offset-4 hover:underline'
			)}
			href="/about"
		>
			About
		</a>
		<a
			class={cn(
				$page.url.pathname === '/contact' ? 'text-blue-500' : 'text-gray-900',
				'text-sm font-medium underline-offset-4 hover:underline'
			)}
			href="/contact"
		>
			Contact
		</a>
	</nav>
</header>
