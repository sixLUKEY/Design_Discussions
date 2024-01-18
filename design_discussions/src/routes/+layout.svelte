<script>
    import "../app.css";

    let routes = [
    {
        name: 'Home',
        href: '/'
    },
    {
        name: 'January',
        href: 'january'
    },
    {
        name: 'February',
        href: 'february'
    }
    ]
</script>

<main class="mx-8 my-4">
    <nav class="my-5">
        <ul class="flex gap-5 ">
            {#each routes as { name, href }}
                <li class=" list-none text-2xl relative overflow-hidden">
                    <a {href}>{name}</a>
                </li>
            {/each}
        </ul>
    </nav>

    <slot />
</main>

<style>
    :global(nav > ul > li::after) {
        content: '';
        position: absolute;
        bottom: -5%;
        left: -100%;
        height: 3px;
        width: 95%;
        background-color: black;
        transition: 200ms;
    }

    :global(nav > ul > li:hover::after) {
        left: 0;
    }
</style>