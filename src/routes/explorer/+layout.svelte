<script lang="ts">
    import { afterNavigate, goto } from '$app/navigation';
    import Navbar from '$lib/navbar.svelte';
    let { children } = $props();

    function navClick(id: string) {
        goto(`/explorer/${id}`);
    }
    let highlightedId = $state('');
    afterNavigate(() => {
        const match = window.location.pathname.match(/^\/explorer\/([^\/]*)/);
        if (match === null) {
            highlightedId = '';
            return;
        }
        highlightedId = match[1];
    });
</script>

<div class="flex w-full gap-4">
    <div>
        <Navbar
            items={[
                { id: 'grocery-list', label: 'Grocery List' },
                { id: 'recipes', label: 'Recipes' },
                { id: 'ingredients', label: 'Ingredients' },
            ]}
            {highlightedId}
            clickHandler={navClick}
        />
    </div>
    <div>{@render children()}</div>
</div>
