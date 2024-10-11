<script lang="ts">
	import Button from '$lib/components/ui/button/button.svelte';
	import {
		Card,
		CardDescription,
		CardHeader,
		CardContent,
		CardFooter,
		CardTitle
	} from '$lib/components/ui/card';
	import { cn } from '$lib/utils';
	import { CheckCircle2 } from 'lucide-svelte';
	import { boolean } from 'zod';

	export let popular: boolean = false;
	export let title: string = 'Default Title';
	export let isYearly: boolean = false; // Provide a default value
	export let yearlyPrice: number = 0;
	export let monthlyPrice: number = 0;
	export let description: string = '';
	export let features: string[] = [];
	export let actionLabel: string = 'Choose Plan';
	export let exclusive: boolean = false;

	console.log(isYearly, 'child');
</script>

<Card
	class={cn(
		`flex w-72 flex-col justify-between py-1 ${popular ? 'border-rose-400' : 'border-zinc-700'} `,
		{
			'animate-background-shine bg-white bg-[length:200%_100%] transition-colors dark:bg-[linear-gradient(110deg,#000103,45%,#1e2631,55%,#000103)]':
				exclusive
		}
	)}
>
	<div>
		<CardHeader class="pb-8 pt-4">
			{#if isYearly && yearlyPrice && monthlyPrice}
				<div class="flex justify-between">
					<CardTitle class="text-lg text-zinc-700 dark:text-zinc-300">{title}</CardTitle>
					<div
						class={cn(
							'h-fit rounded-xl bg-zinc-200 px-2.5 py-1 text-sm text-black dark:bg-zinc-800 dark:text-white',
							{
								'bg-gradient-to-r from-orange-400 to-rose-400 dark:text-black ': popular
							}
						)}
					>
						Save ${monthlyPrice * 12 - yearlyPrice}
					</div>
				</div>
			{:else}
				<CardTitle class="text-lg text-zinc-700 dark:text-zinc-300">{title}</CardTitle>
			{/if}
			<div class="flex gap-0.5">
				<h3 class="text-3xl font-bold">
					{yearlyPrice && isYearly
						? '$' + yearlyPrice
						: monthlyPrice
							? '$' + monthlyPrice
							: 'Custom'}
				</h3>
				<span class="mb-1 flex flex-col justify-end text-sm"
					>{yearlyPrice && isYearly ? '/year' : monthlyPrice ? '/month' : ''}</span
				>
			</div>
			<CardDescription class="h-12 pt-1.5">{description}</CardDescription>
		</CardHeader>

		{#each features as feature}
			<CardContent class="flex flex-col gap-2">
				<div class="flex gap-2">
					<CheckCircle2 size={18} class="my-auto text-green-400" />
					<p class="pt-0.5 text-sm text-zinc-700 dark:text-zinc-300">{feature}</p>
				</div>
			</CardContent>
		{/each}
	</div>
	<CardFooter class="mt-2">
		<Button
			class="relative inline-flex w-full items-center justify-center rounded-md bg-black px-6 font-medium text-white transition-colors  focus:outline-none focus:ring-2 focus:ring-slate-400 focus:ring-offset-2 focus:ring-offset-slate-50 dark:bg-white dark:text-black"
		>
			<div
				class="absolute -inset-0.5 -z-10 rounded-lg bg-gradient-to-b from-[#c7d2fe] to-[#8678f9] opacity-75 blur"
			/>
			{actionLabel}
		</Button>
	</CardFooter>
</Card>
