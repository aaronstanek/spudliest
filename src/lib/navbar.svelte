<script lang="ts">
    type NavItem = {
        id: string;
        label: string;
    };

    let {
        items = [],
        clickHandler,
    }: {
        items: NavItem[];
        clickHandler: (id: string) => void;
    } = $props();
</script>

<aside
    class="h-screen w-50 flex-shrink-0 overflow-y-auto border-r border-gray-200 bg-gray-50"
>
    <nav class="p-4">
        <ul class="flex flex-col space-y-1">
            {#each items as item (item.id)}
                <li>
                    <button
                        class="w-full rounded-md border border-gray-200/80 bg-white px-3 py-2.5 text-left break-words whitespace-normal text-gray-700 shadow-xs transition-all duration-150 ease-in-out hover:border-transparent hover:bg-blue-500 hover:text-white hover:shadow-md"
                        onclick={() => clickHandler(item.id)}
                    >
                        {item.label}
                    </button>
                </li>
            {/each}
        </ul>
    </nav>
</aside>
