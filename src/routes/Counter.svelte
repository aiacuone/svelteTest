<script>
	import Card from '../components/Card.svelte';
	import peopleInitial from '../list.json';

	let people = peopleInitial;

	$: people, console.log('people', ' L9 @ Counter.svelte');
	const onUpdatePerson = ({ uuid, key, value }) => {
		const personIndex = people.findIndex((person) => person.uuid === uuid);
		people[personIndex][key] = value;
	};
</script>

<div class="flex flex-col gap-3">
	<div class="grid  grid-cols-5 gap-3">
		{#each people as person (person.name)}
			<Card {person} {onUpdatePerson} />
		{/each}
	</div>
</div>
