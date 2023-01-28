<script>
	export let isSelected;
	export let onClick;
	export let isFullWidth;
</script>

<button
	on:click={onClick}
	class={`${isSelected ? 'bg-gray-300' : 'bg-gray-200'} p-2 rounded-md ${
		isFullWidth ? 'w-full' : ''
	}`}><slot /></button
>
