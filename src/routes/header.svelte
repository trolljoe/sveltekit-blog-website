<script lang="ts">
    import Toggle from './toggle.svelte'
    import * as config from '$lib/config'
</script>


<nav>
    <a href="/" class="title">
    <b>{config.title}</b>
    </a>

    <ul class="links">
        <li>
            <a class="funny-button" href="/about">[   about   ]</a>
        </li>

    <li>
        <a class="funny-button" href="/contact">[   contact   ]</a>
    </li>

    <li>
        <a class="funny-button" href="/rss.xml" target="_blank">[   rss   ]</a>
    </li>
</ul>



<Toggle />
</nav>

<style>
    nav{
        padding-block: var(--size-7);
    }

    .links {
        margin-block: var(--size-7);
    }

    a {
        color: inherit;
        text-decoration: none;
    }
    .funny-button {
        border: 2px solid transparent;
        padding: 5px 10px;
        background-color: transparent;
        color: var(--button-text-color, green);
        cursor: pointer;
        font-weight: bold;
    }

    .funny-button:hover {
        background-color: var(--button-hover-bg-color, green);
        color: var(--button-hover-text-color, black);
    }

    @media (min-width: 768px) {
        nav {
            display: flex;
            justify-content: space-between;
        }

        .links {
            display: flex;
            gap: var(--size-7);
            margin-block: 0;
        }
    }
    @media (prefers-color-scheme: light) {
        :root {
            --button-text-color: blue;
            --button-hover-bg-color: blue;
            --button-hover-text-color: white;
        }
    }

    /* Dark theme colors */
    @media (prefers-color-scheme: dark) {
        :root {
            --button-text-color: green;
            --button-hover-bg-color: green;
            --button-hover-text-color: black;
        }
    }
</style>
