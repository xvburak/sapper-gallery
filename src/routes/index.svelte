<script>
    const Arena = require('are.na');
    const arena = new Arena({
        accessToken: '402ab5bb9bd011fe5dafbdf0d8acfb039007794df98e3d4d8f74cc9958c295f9'
    });

    let blocks = [];

    arena.channel('sunshine-type').contents({
            page: 1,
            per: 100
        })
        .then(contents => {
            blocks = contents
        })
        .catch(err => console.log(err));

    let checked = false;

</script>

<div>
    <div class="flex justify-between">
        <p>Sunshine Type</p>
        <div class="flex mb-4">
            <label class="cursor-pointer">
              <input
                class="appearance-none checked:bg-black checked:border-transparent focus:outline-none"
                type=radio bind:group={checked} value={true}>grid
            </label>
            <p>&nbsp;/&nbsp;</p>
            <label class="cursor-pointer">
              <input
                class="appearance-none checked:bg-black checked:border-transparent focus:outline-none"
                type=radio bind:group={checked} value={false}>list
            </label>
          </div>
    </div>
    {#if checked}
    <div class="grid grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
        {#each blocks as block}
		   
				{#if block.class === 'Image'}
					<div class="flex flex-col justify-center ">
						<img class="" src="{block.image.display.url}" alt="{block.image.filename}">
					</div>
				{/if}
		{/each}
	</div>
    {:else}
    <table class="w-full table-fixed">
        <tbody>
        {#each blocks as block}
          <tr class="border-b border-black">
            <td class="py-2 w-1/4 md:w-1/6 overflow-hidden overflow-ellipsis whitespace-nowrap">25/10/2000</td>
            <td class="py-2 w-2/4 md:w-3/12 overflow-hidden overflow-ellipsis whitespace-nowrap">{block.title}</td>
            <td class="py-2 w-1/4 md:w-1/6 overflow-hidden overflow-ellipsis whitespace-nowrap">Untersee, Austria</td>
            <td class="py-2 lg:w-5/12 overflow-hidden overflow-ellipsis whitespace-nowrap">summer shadow movement glow reflection trees collision black</td>
          </tr>
        {/each}
        </tbody>
      </table>
    {/if}
  </div>