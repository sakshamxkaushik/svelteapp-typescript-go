<script lang="ts">
	import { scale, fly } from 'svelte/transition';
	import { order } from '../../store/stores';
	import { storeOrder } from '../../data/services';
	import "../../style.css";

	const submit = async () => {
		const id = await storeOrder($order);
		location.href = `/summary/${id}`;
	};
</script>

<style>
	.bg-custom {
	  background-color: #071A34; /* Set the background color to #071A34 */
	  color: #4FDAE3; /* Set text color to white (#FFFFFF) */
	  padding: 2rem;
	}
  
	.bg-button {
	  background-color: #4FDAE3; /* Set the background color for submit button to #172B46 */
	  color: #071A34; /* Set font color for submit button to white (#FFFFFF) */
	}
	.btn-secondary {
	  background-color: #f8fbff; /* Set the background color for submit button to #172B46 */
	  color: #071A34; /* Set font color for submit button to white (#FFFFFF) */
	}
  
	.p-3 {
	  background-color: #172B46; /* Set the background color to #172B46 */
	  padding: 1.5rem;
	}
  .text-center
  {
	background-color: #071A34;
  }

  .p-2
  {
	background-color: #071A34;
  }

  
	/* Add any other CSS styles you need for this component */
  </style>

<div>
	<h3 class="text-center bg-custom text-white p-2">Order Summary</h3>
	<div class="p-3" in:scale|global={{ start: 0.9, duration: 1000 }}>
		<table class="table table-sm table-striped">
			<thead>
				<tr>
					<th>Quantity</th>
					<th>Product</th>
					<th class="text-end">Price</th>
					<th class="text-end">Subtotal</th>
				</tr>
			</thead>
			<tbody>
				{#each $order.orderLines as line}
					<tr>
						<td>{line.quantity}</td>
						<td>{line.product.name}</td>
						<td class="text-end">${line.product.price.toFixed(2)}</td>
						<td class="text-end">${line.total.toFixed(2)}</td>
					</tr>
				{/each}
			</tbody>
			<tfoot>
				<tr>
					<th class="text-end" colSpan="3">Total:</th>
					<th class="text-end">
						<span style="display: inline-block" in:fly|global={{ y: 25, duration: 2000 }}>
							${$order.total.toFixed(2)}
						</span>
					</th>
				</tr>
			</tfoot>
		</table>
	</div>
	<div class="text-center">
		<a href="/products" class="btn btn-secondary m-1"> Back </a>
	
<!-- ... -->
<button class="btn btn-primary m-1 bg-button" on:click={submit}>Submit Order</button>
	</div>
</div>

