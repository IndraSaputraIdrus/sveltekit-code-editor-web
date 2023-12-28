<script lang="ts">
	let myTitle = 'Untitled';

	function handleClick(event: MouseEvent) {
		const element = event.target as HTMLInputElement;
		element.select();
	}
</script>

<div class="grid grid-cols-6 items-center bg-slate-800 px-5 py-2">
	<div class="flex flex-auto space-x-2">
		<div class="h-3 w-3 rounded-full bg-red-500"></div>
		<div class="h-3 w-3 rounded-full bg-yellow-500"></div>
		<div class="h-3 w-3 rounded-full bg-green-500"></div>
	</div>
	<div class="col-span-4 flex justify-center">
		<input
			type="text"
			on:click={handleClick}
			spellcheck="false"
			bind:value={myTitle}
			placeholder="Enter title here"
			class="bg-transparent text-center text-sm font-medium text-slate-600 outline-none placeholder:text-slate-600"
			style={`width: ${myTitle.length > 2 ? myTitle.length : 17}ch`}
		/>
	</div>
</div>
