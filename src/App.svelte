<script>
    export let name;

    import Home from './Home.svelte';
    import About from './About.svelte';
    import Archive from './Archive.svelte';

    let current = 0;
    const switchTo = (newView) => {
        current = newView;
    };
</script>

<style>
	h1 {
		color: white;
	}
    .top {
        margin-bottom: 2rem;
    }
    span {
        text-decoration: underline;
        cursor: pointer;
    }
    .active {
        font-weight: bold;
    }
</style>

<center>
    <div class="top">
            <h1>{name}</h1>
            <span on:click={() => switchTo(0)} class:active={current === 0}>Home</span>
            - 
            <span on:click={() => switchTo(1)} class:active={current === 1}>About</span>
            - 
            <span on:click={() => switchTo(2)} class:active={current === 2}>Archive</span>
    </div>
    {#if current == 0}
        <Home/>
    {:else if current == 1}
        <About/>
    {:else}
        <Archive/>
    {/if}
</center>