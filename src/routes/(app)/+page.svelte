<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import { CardHeader, CardTitle, CardContent } from '$lib/components/ui/card';
	import Card from '$lib/components/ui/card/card.svelte';
	import Input from '$lib/components/ui/input/input.svelte';
	import { Search, Users } from 'lucide-svelte';
	import Award from 'lucide-svelte/icons/award';
	import BookOpen from 'lucide-svelte/icons/book-open';
	import Link from 'lucide-svelte/icons/link';
	const courses = [
		'Web Development',
		'Data Science',
		'Digital Marketing',
		'Graphic Design',
		'Business Analytics',
		'Mobile App Development'
	];
</script>

<div>
	<main class="flex-1">
		<section class="w-full py-12 md:py-24 lg:py-32 xl:py-48">
			<div class="container px-4 md:px-6">
				<div class="flex flex-col items-center space-y-4 text-center">
					<div class="space-y-2">
						<h1
							class="text-3xl font-bold tracking-tighter sm:text-4xl md:text-5xl lg:text-6xl/none"
						>
							Unlock Your Potential with LearnWise
						</h1>
						<p class="mx-auto max-w-[700px] text-gray-500 dark:text-gray-400 md:text-xl">
							Discover thousands of courses taught by expert instructors. Learn at your own pace and
							achieve your goals.
						</p>
					</div>
					<div class="w-full max-w-sm space-y-2">
						<form class="flex space-x-2">
							<Input class="max-w-lg flex-1" placeholder="Search for courses" type="text" />
							<Button type="submit">
								<Search class="mr-2 h-4 w-4" />
								Search
							</Button>
						</form>
					</div>
				</div>
			</div>
		</section>
		<section class="w-full bg-gray-100 py-12 dark:bg-gray-800 md:py-24 lg:py-32">
			<div class="container px-4 md:px-6">
				<h2 class="mb-12 text-center text-3xl font-bold tracking-tighter sm:text-5xl">
					Featured Courses
				</h2>
				<div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
					{#each courses as course, i}
						<Card>
							<CardHeader>
								<CardTitle>{course}</CardTitle>
							</CardHeader>
							<CardContent>
								<p class="text-sm text-gray-500 dark:text-gray-400">
									Learn the fundamentals and advanced techniques in {course.toLowerCase()}.
								</p>
								<Button class="mt-4" variant="outline">Learn More</Button>
							</CardContent>
						</Card>
					{/each}
				</div>
			</div>
		</section>
		<section class="w-full py-12 md:py-24 lg:py-32">
			<div class="container px-4 md:px-6">
				<h2 class="mb-12 text-center text-3xl font-bold tracking-tighter sm:text-5xl">
					Why Choose LearnWise?
				</h2>
				<div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
					<div class="flex flex-col items-center text-center">
						<Users class="mb-4 h-12 w-12 text-primary" />
						<h3 class="mb-2 text-xl font-bold">Expert Instructors</h3>
						<p class="text-gray-500 dark:text-gray-400">
							Learn from industry professionals and subject matter experts.
						</p>
					</div>
					<div class="flex flex-col items-center text-center">
						<BookOpen class="mb-4 h-12 w-12 text-primary" />
						<h3 class="mb-2 text-xl font-bold">Diverse Course Catalog</h3>
						<p class="text-gray-500 dark:text-gray-400">
							Explore a wide range of subjects and skills to learn.
						</p>
					</div>
					<div class="flex flex-col items-center text-center">
						<Award class="mb-4 h-12 w-12 text-primary" />
						<h3 class="mb-2 text-xl font-bold">Certificates</h3>
						<p class="text-gray-500 dark:text-gray-400">
							Earn recognized certificates upon course completion.
						</p>
					</div>
				</div>
			</div>
		</section>
		<section class="w-full bg-gray-100 py-12 dark:bg-gray-800 md:py-24 lg:py-32">
			<div class="container px-4 md:px-6">
				<div class="flex flex-col items-center space-y-4 text-center">
					<div class="space-y-2">
						<h2 class="text-3xl font-bold tracking-tighter sm:text-5xl">Start Learning Today</h2>
						<p
							class="mx-auto max-w-[600px] text-gray-500 dark:text-gray-400 md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed"
						>
							Join millions of learners and start your journey to success with LearnWise.
						</p>
					</div>
					<Button class="w-full sm:w-auto" size="lg">Get Started</Button>
				</div>
			</div>
		</section>
	</main>
	<footer
		class="flex w-full shrink-0 flex-col items-center gap-2 border-t px-4 py-6 sm:flex-row md:px-6"
	>
		<p class="text-xs text-gray-500 dark:text-gray-400">© 2024 LearnWise. All rights reserved.</p>
		<nav class="flex gap-4 sm:ml-auto sm:gap-6">
			<Link class="text-xs underline-offset-4 hover:underline" href="#">Terms of Service</Link>
			<Link class="text-xs underline-offset-4 hover:underline" href="#">Privacy</Link>
		</nav>
	</footer>
</div>
