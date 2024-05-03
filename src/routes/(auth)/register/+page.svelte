<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import { Input } from '$lib/components/ui/input';
	import { registerSchema } from '$lib/schema.js';
	import { superForm } from 'sveltekit-superforms';
	import { zodClient } from 'sveltekit-superforms/adapters';
	import { toast } from 'svelte-sonner';
	import * as Form from '$lib/components/ui/form';
	import { Loader2 } from 'lucide-svelte';
	export let data;

	const form = superForm(data.form, {
		validators: zodClient(registerSchema),
		onUpdated({ form }) {
			if (form.message) {
				if (!form.valid) {
					toast.error(form.message);
				}
				if (form.valid) {
					toast.success(form.message);
				}
			}
		}
	});

	const { form: formData, enhance, delayed } = form;
</script>

<Card.Root class="mx-auto max-w-sm">
	<Card.Header>
		<Card.Title class="text-xl">Sign Up</Card.Title>
		<Card.Description>Enter your information to create an account</Card.Description>
	</Card.Header>
	<Card.Content>
		<div class="grid gap-4">
			<form method="POST" use:enhance action="/register">
				<div class="grid grid-cols-2 gap-4">
					<Form.Field {form} name="firstName" class="grid ">
						<Form.Control let:attrs>
							<Form.Label>FirstName</Form.Label>
							<Input {...attrs} bind:value={$formData.firstName} />
						</Form.Control>
						<Form.Description />
						<Form.FieldErrors />
					</Form.Field>
					<Form.Field {form} name="lastName" class="grid ">
						<Form.Control let:attrs>
							<Form.Label>LastName</Form.Label>
							<Input {...attrs} bind:value={$formData.lastName} />
						</Form.Control>
						<Form.Description />
						<Form.FieldErrors />
					</Form.Field>
				</div>
				<Form.Field {form} name="email" class="grid ">
					<Form.Control let:attrs>
						<Form.Label>Email</Form.Label>
						<Input {...attrs} bind:value={$formData.email} />
					</Form.Control>
					<Form.Description />
					<Form.FieldErrors />
				</Form.Field>
				<Form.Field {form} name="password" class="grid ">
					<Form.Control let:attrs>
						<Form.Label>Password</Form.Label>
						<Input type="password" {...attrs} bind:value={$formData.password} />
					</Form.Control>
					<Form.Description />
					<Form.FieldErrors />
				</Form.Field>
				<Form.Field {form} name="passwordConfirm" class="grid ">
					<Form.Control let:attrs>
						<Form.Label>Confirm password</Form.Label>
						<Input type="password" {...attrs} bind:value={$formData.passwordConfirm} />
					</Form.Control>
					<Form.Description />
					<Form.FieldErrors />
				</Form.Field>
				<Form.Button class="w-full"
					>{#if $delayed}
						<Loader2 class="size-6 animate-spin " />
					{:else}
						Register
					{/if}</Form.Button
				>
			</form>
		</div>
		<div class="mt-4 text-center text-sm">
			Already have an account?
			<a href="/login" class="underline"> Sign in </a>
		</div>
	</Card.Content>
</Card.Root>
