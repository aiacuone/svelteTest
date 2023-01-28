<script>
	export let person;
	export let onFavourite;

	const { isFavourite, uuid, name, image } = person;
	let favouriteButtonColor = 'red';

	const onFavouriteLocal = () => {
		favouriteButtonColor = isFavourite ? 'green' : 'blue';
		onFavourite({ id: uuid, boolean: !isFavourite });
	};

	const mapArray = { name, uuid, isFavourite };
</script>

<div class="border-2 border-black p-4">
	<ul>
		{#each Object.entries(mapArray) as [key, value]}
			<li>{key}: {value}</li>
		{/each}
	</ul>
	<img src={image} alt="test" />

	<button on:click={onFavouriteLocal} class={`w-full py-2 bg-${favouriteButtonColor}-500`}
		>Favourite</button
	>
</div>
