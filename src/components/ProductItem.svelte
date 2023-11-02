<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import type { Product } from '../data/entities';
	import { OrderLine } from '../data/entities';

	const dispatch = createEventDispatcher<{ addToCart: OrderLine }>();

	export let product: Product;
	let quantity: string;

	const handleAddToCart = () => {
		dispatch('addToCart', new OrderLine(product, Number(quantity)));
	};
</script>

<style>
	.card {
		background-color: #172B46; /* Set the background color for the card to #172B46 */
	}

	.card-text {
		color: #A5B6D4; /* Set the text color for product description to #A5B6D4 */
	}

	.btn-add-to-cart {
		background-color: #4FDAE3; /* Set the background color to #4FDAE3 */
		color: #000000; /* Set text color to white (#FFFFFF) */
	}
	 .bg-custom {
		background-color: #172B46;
		color: #A5B6D4;

	 }
	 .bg-pill {
		background-color: #0A1930;
		font-family: 'Poppins', sans-serif;
		font-size: small;
		font-weight: lighter;
	 }
	 .bg-quantity {
		background-color: #0A1930;
		color: #ffff;
		font-family: 'Poppins', sans-serif;
		font-size: small;
	
	}
	
</style>

<div class="card m-1 p-1 bg-custom">
	<h4>
		{product.name}
		<span class="badge rounded-pill bg-pill float-end">
			${product.price.toFixed(2)}
		</span>
	</h4>
	<div class="card-text bg-custom p-1">
		{product.description}
		<button class="btn btn-add-to-cart btn-sm float-end" on:click={handleAddToCart}>
			Add To Cart
		</button>
		<select class="form-control-inline float-end m-1 bg-quantity " bind:value={quantity}>
			<option>1</option>
			<option>2</option>
			<option>3</option>
		</select>
	</div>
</div>
