<script>
    import * as apps from '../apps.json'

    const change = (array) => {
        const first = array[0];
        array.shift();
        array.push(first);
    }

    const next = () => {
        change(apps.default);
        apps.default = apps.default;
    }
</script>

<style>
    .container{
        display: inline-block;
        width: 1400px;
        height: 1000px;
        text-align: center;
    }

    .link{
        display: grid;
        place-items: center;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        color: #2E3440;
    }

    .link:hover{
        cursor: pointer;
    }

    .app{
        position: relative;
        display: inline-block;
        place-content: center;
        font-size: 300px;
        border-radius: 20px;
        background-color: var(--cardBackground);
        margin: 20px;
        width: 400px;
        height: 400px;
        transition: 0.2s;
    }

    .app:hover{
        background-color: var(--temperature);
    }

    .svg {
        width: 80%;
    }
</style>

<div class="container">
    {#if apps.default.length>6}
        {#each apps.default.slice(0,5) as app}
            <div class="app"><a class="link" href = {app.url}>
                {#if app.logo.search(".svg")!=-1}
                    <img src = "/images/{app.logo}" class = "svg" alt= {app.logo}>
                {:else}
                    {app.logo}
                {/if}
            </a></div>
        {/each}
        <div class="app" on:click={next}><a class = "link">...</a></div>
    {:else}
        {#each apps.default as app}
            <div class="app"><a class="link" href = {app.url}>
                {#if app.logo.search(".svg")!=-1}
                    <img src = "/images/{app.logo}" class = "svg" alt= {app.logo}>
                {:else}
                    {app.logo}
                {/if}
            </a></div>
        {/each}
    {/if}

</div>