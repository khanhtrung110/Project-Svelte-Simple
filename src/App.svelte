<script>
	import Product from "./Product.svelte";
	import Modal from "./Modal.svelte";
	let showModel = false;
	let closable = false;
	let products = [
		{
			id: "p1",
			title: "Mlem",
			price: 9.99,
		},
	];
</script>

{#each products as product}
	<Product
		{...product}
		on:add-to-cart={() => alert("Add to cart!")}
		on:delete={() => {
			alert("Delete");
		}}
	/>
{/each}
<button
	on:click={() => {
		showModel = true;
	}}>ShowModel</button
>
{#if showModel}
	<Modal
		on:cancel={() => (showModel = false)}
		on:close={() => (showModel = false)}
		let:didAgree={closable}
		>
		<h1 slot="header">Hello!</h1>
		<p>This Works!</p>
		<button slot="footer" on:click={() => (showModel = false)} disabled={!closable} >Confirm</button>
	</Modal>
{/if}

<style>
</style>
