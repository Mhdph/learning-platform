<script lang="ts">
	import Button from '$lib/components/ui/button/button.svelte';
	import Input from '$lib/components/ui/input/input.svelte';
	import Label from '$lib/components/ui/label/label.svelte';
	import * as Form from '$lib/components/ui/form';
	import { zodClient } from 'sveltekit-superforms/adapters';
	import { superForm } from 'sveltekit-superforms';
	import { loginSchema } from '$lib/schema.js';
	import { Loader2 } from 'lucide-svelte';
	export let data;
	const form = superForm(data.form, {
		validators: zodClient(loginSchema)
	});
	const { form: formData, enhance, delayed } = form;
</script>

<div class="mx-auto grid w-[350px] gap-6">
	<div class="grid gap-2 text-center">
		<h1 class="text-3xl font-bold">Login</h1>
		<p class="text-balance text-muted-foreground">
			Enter your email below to login to your account
		</p>
	</div>
	<div class="grid gap-4">
		<form method="POST" use:enhance action="/login ">
			<Form.Field {form} name="email" class="grid gap-2">
				<Form.Control let:attrs>
					<Form.Label>Email</Form.Label>
					<Input {...attrs} bind:value={$formData.email} />
				</Form.Control>
				<Form.Description />
				<Form.FieldErrors />
			</Form.Field>
			<Form.Field {form} name="password" class="grid gap-2">
				<Form.Control let:attrs>
					<Form.Label>password</Form.Label>
					<Input type="password" {...attrs} bind:value={$formData.password} />
				</Form.Control>
				<Form.Description />
				<Form.FieldErrors />
			</Form.Field>

			<Button type="submit" class="flex w-full items-center">
				{#if $delayed}
					<Loader2 class="size-6 animate-spin" />
				{/if}
				Login
			</Button>
		</form>
	</div>
	<div class="mt-4 text-center text-sm">
		Don&apos;t have an account?
		<a href="/register" class="underline"> Sign up </a>
	</div>
</div>
