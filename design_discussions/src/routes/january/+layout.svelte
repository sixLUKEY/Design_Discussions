<script>
    let weeks = [
        {
            name: '1',
            href: '1'
        },
        {
            name: '2',
            href: '2'
        }
    ]
</script>

<h1 class="text-5xl">
    DESIGN IN JANUARY?!
</h1>

<nav class="my-5">
    <ul class="flex gap-5">
        {#each weeks as { name, href }}
        <li>
            <a href={`/january/${href}`}>Week {name}</a>
        </li>
        {/each}
    </ul>
</nav>

<slot/>