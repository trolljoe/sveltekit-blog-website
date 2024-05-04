<script lang="ts">
    import { fly } from 'svelte/transition'
    import { Moon, Sun } from 'lucide-svelte'
    import { theme, toggleTheme } from '$lib/theme'
</script>

<div on:click={toggleTheme} aria-label="Toggle theme" role="button" style="cursor: pointer;">
    {#if $theme === 'dark'}
        <div in:fly={{ y: 10 }}>
            <Sun />
            <span>[   light   ]</span>
        </div>
    {:else}
        <div in:fly={{ y: -10 }}>
            <Moon />
            <span>[   dark   ]</span>
        </div>
    {/if}
</div>

<style>
    div {
        border: 2px solid transparent;
        padding: 5px 10px;
        background-color: transparent;
        color: var(--button-text-color, green);
        font-weight: bold;
        display: inline-flex;
    }

    div:hover {
        background-color: var(--button-hover-bg-color, green);
        color: var(--button-hover-text-color, black);
    }

    div > * {
        display: flex;
        gap: var(--size-2);
    }
</style>
