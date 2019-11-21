<script>
    export let name;

    import Home from './Home.svelte';
    import About from './About.svelte';
    import Archive from './Archive.svelte';

    let current = 0;
    const switchTo = (newView) => {
        current = newView;
    };

    let theme = "light";
    if (window.localStorage.getItem("theme") === "dark") {
        theme = "dark";
    }

    const toggleTheme = () => {
        theme = (theme === "light") ? "dark" : "light";
        window.localStorage.setItem("theme", theme);
    }
</script>

<style>
    .everything {
        background-color: white;
        min-height: 100%;
        color: black;
    }
    button {
        padding: 20px;
        color: black;
        background-color: white;
    }
	h1 {
        color: #73007d;
        margin: 0;
	}
    .top {
        margin-bottom: 2rem;
        background-color: white;
        color: black;
    }
    span {
        text-decoration: underline;
        cursor: pointer;
    }
    .active {
        font-weight: bold;
    }
    .dark, .dark .top, .dark button {
        background-color: black;
        color: white;
    }
    .dark h1 {
        color: white;
    }
</style>

<div class="everything" class:dark={theme === "dark"}>
    <center>
        <div class="top">
                <h1>{name}</h1>
                <span on:click={() => switchTo(0)} class:active={current === 0}>Home</span>
                - 
                <span on:click={() => switchTo(1)} class:active={current === 1}>About</span>
                - 
                <span on:click={() => switchTo(2)} class:active={current === 2}>Archive</span>
        </div>
        <button on:click={toggleTheme}>Turn Lights {theme === "light" ? "Off" : "On"} 💡</button>
        {#if current == 0}
            <Home/>
        {:else if current == 1}
            <About/>
        {:else}
            <Archive/>
        {/if}
    </center>
</div>