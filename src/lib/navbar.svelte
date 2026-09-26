<script lang="ts">
    import { blueBackground, whiteBackground } from './navbar';

    type NavItem = {
        id: string;
        label: string;
    };

    let {
        items = [],
        highlightedId,
        clickHandler,
    }: {
        items: NavItem[];
        highlightedId: string;
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
                        class={item.id === highlightedId
                            ? blueBackground
                            : whiteBackground}
                        onclick={() => clickHandler(item.id)}
                    >
                        {item.label}
                    </button>
                </li>
            {/each}
        </ul>
    </nav>
</aside>
