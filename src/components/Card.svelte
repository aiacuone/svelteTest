<script>
	export let person;
	export let onUpdatePerson;
	let { isFavourite } = person;
	console.log('person', ' L29 @ card.svelte');

	const onFavourite = () => {
		onUpdatePerson({
			uuid: person.uuid,
			key: 'isFavourite',
			value: !isFavourite
		});
	};
</script>

<div class="flex flex-col gap-3 border-2 border-black p-3">
	<h1>{person.name}</h1>
	<p>{isFavourite}</p>
	<button class={`bg-gray-${isFavourite ? '300' : '200'} p-2 rounded-md`} on:click={onFavourite}
		>favourite</button
	>
	<img src={person.image} alt="test" />
</div>
