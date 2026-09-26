<script lang="ts">
    import { goto } from '$app/navigation';
    import Navbar from '$lib/navbar.svelte';
    import '../app.css';
    let { children } = $props();

    function navClick(id: string) {
        goto(`/${id}`);
    }
</script>

<div class="flex w-full gap-4">
    <div>
        <Navbar
            items={[
                { id: 'grocery-list', label: 'Grocery List' },
                { id: 'recipes', label: 'Recipes' },
                { id: 'ingredients', label: 'Ingredients' },
            ]}
            clickHandler={navClick}
        />
    </div>
    <div>{@render children()}</div>
</div>
