<script>
    import "../app.css";

    let routes = [
    {
        name: 'home',
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

<main>
    <nav>
        <ul>
            {#each routes as { name, href }}
                <li class=" list-none text-2xl">
                    <a {href}>{name}</a>
                </li>
            {/each}
        </ul>
    </nav>

    <slot />
</main>