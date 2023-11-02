<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import { selectedCategory } from '../store/stores';

	const dispatch = createEventDispatcher<{ selectCategory: string }>();

	export let categories: string[] = [];

	const selectCategory = (category: string) => {
		dispatch('selectCategory', category);
	};

	const getButtonClasses = (category: string): string => {
		const btnClass = $selectedCategory === category ? 'btn-primary' : 'btn-secondary';
		return `btn ${btnClass}`;
	};
</script>

<style>
	.d-grid {
		color: #FFFFFF; /* Set text color to white (#FFFFFF) */
	}

	/* Set the default button background color to #172B46 */
	button {
		background-color: #172B46;
		border: #4FDAE3;
	}

	/* Set product description color to #A5B6D4 */
	.product-description {
		color: #A5B6D4;
	}

	/* Set the hover color for .btn-primary to #4FDAE3 */
	.btn-primary:hover {
		background-color: #4FDAE3;
	}
</style>

<div class="d-grid gap-2">
	{#each categories as c}
		<button class={getButtonClasses(c)} on:click={() => selectCategory(c)}>
			{c}
		</button>
	{/each}
</div>
