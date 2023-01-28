<script>
	import Button from './Button.svelte';

	export let person;
	export let onUpdatePerson;
	export let allGroups;
	export let onAddGroup;

	console.log('person', ' L29 @ card.svelte');

	const onFavourite = () => {
		onUpdatePerson({
			uuid: person.uuid,
			key: 'isFavourite',
			value: !person.isFavourite
		});
	};

	const onGroups = () => {
		onUpdatePerson({
			uuid: person.uuid,
			key: 'groups',
			value: [...person.groups, `group${person.groups.length}`]
		});
		onAddGroup(`group${allGroups.length}`);
	};
</script>

<div class="flex flex-col gap-3 border-2 border-black p-3">
	<h1>{person.name}</h1>
	<p>{person.isFavourite}</p>
	<Button isSelected={person.isFavourite} onClick={onFavourite}>Favourite</Button>
	<img src={person.image} alt="test" />
	<div>
		<h1>Groups</h1>
		<Button onClick={onGroups} isFullWidth>Add Group</Button>
		<ul>
			{#each allGroups as group}
				<li>
					{group}
				</li>
			{/each}
		</ul>
	</div>
</div>
