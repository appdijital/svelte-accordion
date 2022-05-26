<script>
    import { slide } from 'svelte/transition';
    let visible = true;
    let sections = [
        {
            id: 1,
            title: "Section 1",
            content: "Section 1 Area",
            active: false,
        },
        {
            id: 2,
            title: "Section 2",
            content: "Section 2 Area",
            active: true,
        },
        {
            id: 3,
            title: "Section 3",
            content: "Section 3 Area",
            active: false,
        }
    ]

    const expand = (section) => {
        sections = sections.map(s => {
            s.active = false
            if (s.id === section.id) {
                s.active = true
            }
            return s
        })
    }
</script>


<div class="block">
    <ul class="block w-11/12 my-4 mx-auto" >

        {#each sections as section}
            <li class="flex align-center flex-col">
                <button on:click={() => expand(section) }>{section.title}</button>
                {#if section.active}
                    <div class="cursor-pointer mb-2 px-5 py-3 m bg-indigo-300 text-white text-center inline-block hover:opacity-75 hover:shadow hover:-mb-3 rounded" transition:slide>
                        <p>{section.content}</p>
                    </div>
                {/if}
            </li>
        {/each}

    </ul>
</div>
