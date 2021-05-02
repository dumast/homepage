<script>
    import App from '../App.svelte';
import * as apps from '../apps.json'

    console.log(apps.default);
    const change = (array) => {
        console.log(array)
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

    .app{
        position: relative;
        display: inline-block;
        place-content: center;
        font-size: 300px;
        border-radius: 20px;
        background-color: var(--blue);
        margin: 20px;
        width: 400px;
        height: 400px;
    }

    .svg {
        width: 80%;
    }
</style>

<div class="container">
    {#if apps.default.length>6}
        {#each apps.default.slice(0,5) as app}
            <a href = {app.url}><div class="app">
                {#if ".svg" in app.logo}
                    <img src = {app.logo} alt = {app.logo}>
                {:else}
                    {app.logo}
                {/if}
                </div></a>
        {/each}
        <div class="app" on:click={next}>...</div>
    {:else}
        {#each apps.default as app}
            <div class="app"><a class="link" href = {app.url}>
                {#if app.logo.search(".svg")!=-1}
                    <img src = {`/images/${app.logo}`} class = "svg" alt= {app.logo}>
                {:else}
                    {app.logo}
                {/if}
            </a></div>
        {/each}
    {/if}

</div>