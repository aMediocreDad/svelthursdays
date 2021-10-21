<script>
	import ShoppingCart from "$lib/components/ShoppingCart.svelte";
	import { writable } from "svelte/store";

	const cart = writable([
		{
			name: "Nintendo Switch OLED 2021",
			image: "/images/switch.webp",
			description: "Nintendo Switch with OLED-Display, 64GB internal storage",
			sku: "0934192",
			price: 499,
			cart: {
				count: 1
			}
		},
		{
			name: "Metroid Dread",
			image: "/images/dread.webp",
			description: "Hottest Nintendo Switch game",
			sku: "10329362",
			price: 59.98,
			cart: {
				count: 1
			}
		}
	]);
</script>

<ShoppingCart {cart} />
