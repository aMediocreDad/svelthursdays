<script>
	import { derived } from "svelte/store";
	export let cart;

	const total = derived(cart, (cart) =>
		cart.reduce((acc, item) => {
			return acc + item.price * item.cart.count;
		}, 0)
	);
</script>

<aside
	id="shopping-cart"
	class="max-w-md px-8 py-6 grid grid-flow-row gap-10 bg-gray-50 bg-opacity-50 text-gray-900 rounded-xl shadow-lg"
>
	<h3 class="text-center font-bold text-2xl text-gray-800">Shopping Cart</h3>
	<ol type="list" class="grid grid-flow-row gap-8">
		{#each $cart as { sku, image, description, name, cart, price } (sku)}
			<li class="grid grid-cols-4 grid-rows-2 items-center">
				<a href="/products/{sku}" class="row-span-2 mr-4"
					><img src={image} alt="{name} product image" width="150" class="drop-shadow-lg" /></a
				>
				<a href="/products/{sku}" class="col-span-2 self-end"
					><h4 class="font-semibold hover:underline">{name.slice(0, 20)}</h4></a
				>
				<p class="font-semibold text-right self-end">${price}</p>
				<p class="text-sm col-span-2 self-start">{description.slice(0, 30)}...</p>
				<div class="text-right self-start">
					<span class="text-sm">Qty:</span>
					<input
						class="text-sm h-8 bg-gray-100 bg-opacity-40 font-semibold border rounded-lg ml-1 mt-1 pr-1"
						bind:value={cart.count}
						type="number"
						min="0"
					/>
				</div>
			</li>
		{/each}
	</ol>

	<div class="text-right">
		<span>Total:</span> <span class="font-semibold ml-1">${$total}</span>
	</div>
	<button
		class="bg-gray-800 bg-opacity-60 p-2 px-8 m-auto border-2 border-gray-200 rounded-lg font-semibold text-gray-100 shadow-md  hover:bg-gray-200 hover:text-gray-900"
		>Checkout</button
	>
</aside>

<style>
	input {
		text-align: center;
		max-width: 2.8rem;
	}

	input[type="number"]::-webkit-inner-spin-button,
	input[type="number"]::-webkit-outer-spin-button {
		appearance: caret;
	}
</style>
