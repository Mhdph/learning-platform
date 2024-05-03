<script lang="ts">
	import mahdi from '$lib/assets/images/authpic.webp';
</script>

<div class="h-screen w-full lg:grid lg:min-h-[600px] lg:grid-cols-2 xl:min-h-[800px]">
	<div class="flex items-center justify-center py-12">
		<slot />
	</div>
	<div class="hidden bg-muted lg:block">
		<img
			src={mahdi}
			alt="placeholder"
			width="1920"
			height="1080"
			class="h-full w-full object-fill dark:brightness-[0.2] dark:grayscale"
		/>
	</div>
</div>
