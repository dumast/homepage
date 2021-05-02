<script>
    import Clock from './Clock.svelte'
    import { onMount } from 'svelte';

    function addZero(i) {
        if (i < 10) {
            i = "0" + i;
        }
        return i;
    }   
    let time = new Date();
    $: hours = addZero(time.getHours());
    $: minutes = addZero(time.getMinutes());
    $: months = addZero(time.getMonth());
    $: days = addZero(time.getDate());
    $: years = time.getFullYear();

    onMount(() => {
        const interval = setInterval(() => {
            time = new Date();
        }, 1000);

        return () => {
            clearInterval(interval);
        };
    });
</script>

<style>
    .container{
        width: 400px;
        height: 1000px;
        display: inline-flex;
        flex-direction: column;
    }
    .time{
        width: 100%;
        font-size: 1.4em;
        margin: 0;
        color: var(--green);
        text-align: center;
    }
    .date{
        font-size: 0.6em;
        margin: 0;
        text-align: center;
        color: var(--orange);
    }
</style>

<div class="container">
    <Clock/>
    <h2 class="time">{hours}:{minutes}</h2>
    <p class="date">
        {months}/{days}/{years}</p>
</div>