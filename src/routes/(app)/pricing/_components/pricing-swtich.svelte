<script lang="ts">
	import { Tabs, TabsList, TabsTrigger } from '$lib/components/ui/tabs';
	import { createEventDispatcher } from 'svelte';

	export let onSwitch: (value: string | undefined) => void;

	const dispatch = createEventDispatcher();

	function handleChange(value: string | undefined) {
		onSwitch(value);
		dispatch('change', value);
	}
</script>

<Tabs
	value="0"
	class="mx-auto flex items-center justify-center pb-3"
	onValueChange={(event) => handleChange(event)}
>
	<TabsList class="px-2 py-6">
		<TabsTrigger value="0" class="text-base">Monthly</TabsTrigger>
		<TabsTrigger value="1" class="text-base">Yearly</TabsTrigger>
	</TabsList>
</Tabs>
