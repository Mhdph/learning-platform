<script lang="ts">
	import PricingCard from './_components/pricing-card.svelte';
	import PricingHeader from './_components/pricing-header.svelte';
	import PricingSwtich from './_components/pricing-swtich.svelte';
	import { onMount } from 'svelte';

	let isYearly = false;

	const togglePricingPeriod = (value: string | undefined) => {
		isYearly = parseInt(value!) === 1;
	};

	console.log(isYearly, 'parent');
	const plans = [
		{
			title: 'Basic',
			monthlyPrice: 10,
			yearlyPrice: 100,
			description: 'Essential features you need to get started',
			features: [
				'Example Feature Number 1',
				'Example Feature Number 2',
				'Example Feature Number 3'
			],
			actionLabel: 'Get Started'
		},
		{
			title: 'Pro',
			monthlyPrice: 25,
			yearlyPrice: 250,
			description: 'Perfect for owners of small & medium businessess',
			features: [
				'Example Feature Number 1',
				'Example Feature Number 2',
				'Example Feature Number 3'
			],
			actionLabel: 'Get Started',
			popular: true
		},
		{
			title: 'Enterprise',
			price: 'Custom',
			description: 'Dedicated support and infrastructure to fit your needs',
			features: [
				'Example Feature Number 1',
				'Example Feature Number 2',
				'Example Feature Number 3',
				'Super Exclusive Feature'
			],
			actionLabel: 'Contact Sales',
			exclusive: true
		}
	];
</script>

<section>
	<PricingHeader title="Pricing Plans" subtitle="Choose the plan that's right for you" />
	<PricingSwtich onSwitch={togglePricingPeriod} />
	<section class="mt-8 flex flex-col justify-center gap-8 sm:flex-row sm:flex-wrap">
		{#each plans as plan}
			<PricingCard {...plan} {isYearly} />
		{/each}
	</section>
</section>
