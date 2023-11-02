<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import { order } from '../store/stores';
	import "../style.css"
  
	$: count = $order.productCount || 0;
	$: displayText1 = count === 0 ? '(No Selection)' : `${count} product(s), `;
	$: displayText2 = count === 0 ? '' : `$${$order.total.toFixed(2)}`;
  </script>
  
  <style>
	.bg-header {
		background-color: #071A34;  /* Set the background color for the header to #071A34 */
		color: #FFFFFF; /* Set text color to white (#FFFFFF) */
	}
	.text-end {
		background-color: #071A34;
		color: #FFFFFF; /* Set text color to white (#FFFFFF) */
	}
	.bg-secondary {
		background-color: #172B46; /* Set the background color for the header to #172B46 */
	}
	.bg-div {
		background-color: #071A34; /* Set the background color of the div to #071A34 */
		border: 1px solid #697D99; /* Set the border color to #697D99 */
	}
	.btn-primary
	{
		background-color: #4FDAE3; /* Set the background color for the submit button to #4FDAE3 */
		color: #071A34; /* Set text color to white (#FFFFFF) */
		border: #697D99;
	}
	.bg-color
	{
		background-color: #071A34; /* Set the background color to #071A34 */
		border: #071A34;
	}
</style>
  
  <div class="p-1 bg-color bg-secondary text-dark text-end bg-header ">
	{#key displayText1}
	  <span style="display: inline-block" in:fade|global={{ duration: 500 }}>
		{displayText1}
	  </span>
	{/key}
	{#key displayText2}
	  <span style="display: inline-block" in:fly|global={{ y: -50, duration: 500, easing: quintOut }}>
		{displayText2}
	  </span>
	{/key}
	<a href="/order" class="btn btn-sm btn-primary btn-4FDAE3 m-1 s-c1MG4BWNDc59">Submit Order</a>
</div>
<div class="p-1 bg-div border-bottom text-dark text-end">
  </div>
  