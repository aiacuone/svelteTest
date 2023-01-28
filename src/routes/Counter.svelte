<script>
	import Card from '../components/Card.svelte';
	import peopleInitial from '../list.json';

	let input = '';
	let people = peopleInitial;

	const onChange = (e) => (input = e.target.value);

	const onFavourite = ({ id, boolean }) => {
		const objIndex = people.findIndex((obj) => obj.uuid === id);

		let updatedPeople = [...people];
		updatedPeople[objIndex].isFavourite = boolean;
		people = updatedPeople;
		console.log({ updatedPeople }, ' L20 @ Counter.svelte');
	};
</script>

<div class="flex flex-col gap-3">
	<div class="flex gap-3">
		<input on:input={onChange} value={input} />
		<button class="bg-gray-300 p-2">submit</button>
	</div>
	<div class="grid  grid-cols-5 gap-3">
		{#each people as person (person.name)}
			<Card {person} {onFavourite} />
		{/each}
	</div>
</div>
