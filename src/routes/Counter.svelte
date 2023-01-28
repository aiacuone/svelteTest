<script>
	import Card from '../components/Card.svelte';
	import peopleInitial from '../list.json';

	let people = peopleInitial;

	const getAllGroups = () => {
		return people.reduce((initArr, person) => {
			person.groups.forEach((group) => {
				if (!initArr.includes(group)) initArr.push(group);
			});
			return initArr;
		}, []);
	};

	let allGroups = getAllGroups();

	console.log('people', ' L6 @ Counter.svelte');

	$: people, (allGroups = getAllGroups());
	$: people, console.log('people', ' L6 @ Counter.svelte');

	const onUpdatePerson = ({ uuid, key, value }) => {
		const personIndex = people.findIndex((person) => person.uuid === uuid);
		people[personIndex][key] = value;
	};
</script>

<div class="flex flex-col gap-3">
	<div class="grid  grid-cols-5 gap-3">
		{#each people as person (person.uuid)}
			<Card {person} {onUpdatePerson} {allGroups} />
		{/each}
	</div>
</div>
