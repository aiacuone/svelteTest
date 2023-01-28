<script>
	import Card from '../components/Card.svelte';
	import peopleInitial from '../list.json';

	let people = peopleInitial;

	let allGroups = people.reduce((initArr, person) => {
		person.groups.forEach((group) => {
			if (!initArr.includes(group)) initArr.push(group);
		});
		return initArr;
	}, []);

	console.log('people', ' L6 @ Counter.svelte');

	$: people, console.log('people', ' L6 @ Counter.svelte');

	const onUpdatePerson = ({ uuid, key, value }) => {
		const personIndex = people.findIndex((person) => person.uuid === uuid);
		people[personIndex][key] = value;
	};

	const onAddGroup = (group) => {
		allGroups = [...allGroups, group];
	};
</script>

<div class="flex flex-col gap-3">
	<div class="grid  grid-cols-5 gap-3">
		{#each people as person (person.uuid)}
			<Card {person} {onUpdatePerson} {allGroups} {onAddGroup} />
		{/each}
	</div>
</div>
