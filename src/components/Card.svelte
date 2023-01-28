<script>
	export let person;
	export let onUpdatePerson;

	console.log('person', ' L29 @ card.svelte');

	const onFavourite = () => {
		onUpdatePerson({
			uuid: person.uuid,
			key: 'isFavourite',
			value: !person.isFavourite
		});
	};
</script>

<div class="flex flex-col gap-3 border-2 border-black p-3">
	<h1>{person.name}</h1>
	<p>{person.isFavourite}</p>
	<button
		class={`bg-gray-${person.isFavourite ? '300' : '200'} p-2 rounded-md`}
		on:click={onFavourite}>favourite</button
	>
	<img src={person.image} alt="test" />
</div>
