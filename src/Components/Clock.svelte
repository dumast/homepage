<script>
    import { onMount } from 'svelte';

    let time = new Date();
    // these automatically update when `time`
    // changes, because of the `$:` prefix
    $: hours = time.getHours();
    $: minutes = time.getMinutes();
    $: seconds = time.getSeconds();

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
    svg {
		width: 100%;
		height: 100%;
	}

	.clock-face {
		stroke: var(--purple);
		fill: none;
        stroke-width: 3;
	}

	.hour {
		stroke: var(--purple);
        stroke-width: 3;
        stroke-linecap: round;
	}

	.minute {
		stroke: var(--purple);
        stroke-width: 3;
        stroke-linecap: round;
	}
</style>

<div class="clock">
    <svg viewBox='-50 -50 100 100'>
        <circle class='clock-face' r='48'/>

        <!-- hour hand -->
        <line
            class='hour'
            y1='0'
            y2='-25'
            transform='rotate({30 * hours + minutes / 2})'
        />

        <!-- minute hand -->
        <line
            class='minute'
            y1='0'
            y2='-35'
            transform='rotate({6 * minutes + seconds / 10})'
        />
    </svg>
</div>