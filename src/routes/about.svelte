<script>
	const Arena = require('are.na');
	const arena = new Arena();

	let blocks = [];

	// arena.channel('capsule-wardrobe-research-mood')
	// 	.get()
	// 	.then(chan => {
	// 		blocks = chan.contents;
	// 		console.log(chan.contents)
	// 	});
   arena.channel('capsule-wardrobe-research-mood').contents({page: 1, per: 100})
		.then(contents => { blocks = contents })
		.catch(err => console.log(err));
</script>

<div>
	<div class="grid grid-cols-5 gap-8">
		{#each blocks as block}
		   
				{#if block.class === 'Image'}
					<div class="flex flex-col justify-center">
						<img src="{block.image.display.url}" alt="{block.image.filename}">
					</div>
				{/if}
	   
		{:else}
		<!-- this block renders when users.length === 0 -->
			<p>loading...</p>
		{/each}
		</div>
  </div>