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

<h1>
    DESIGN IN JANUARY?!
</h1>

<nav>
    <ul>
        {#each weeks as { name, href }}
        <li>
            <a href={`/january/${href}`}>Week {name}</a>
        </li>
        {/each}
    </ul>
</nav>

<slot/>