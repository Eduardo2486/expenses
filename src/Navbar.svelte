<script>
	export let showForm;
</script>
<nav class="nav">
	<div class="nav-center">
		<h1>Budget Calculator</h1>

		<button type="button" class="nav-btn"  on:click={()=>showForm()}>
			Add Item
		</button>
	</div>
</nav>