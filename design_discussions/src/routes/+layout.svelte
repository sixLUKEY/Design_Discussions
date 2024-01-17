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
                <li class=" list-none text-2xl">
                    <a {href}>{name}</a>
                </li>
            {/each}
        </ul>
    </nav>

    <slot />
</main>