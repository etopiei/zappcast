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
    div {
        display: flow-root;
        height: 100%;
        background-color: white;
        color: black;
    }
    button {
        position: absolute;
        right: 10px;
        top: 10px;
        padding: 20px;
        color: black;
        background-color: white;
    }
	h1 {
		color: #73007d;
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
    .dark, .dark .top, .dark button {
        background-color: black;
        color: white;
    }
    .dark h1 {
        color: white;
    }
</style>

<div class:dark={theme === "dark"}>
    <button on:click={toggleTheme}>Turn Lights {theme === "light" ? "Off" : "On"} 💡</button>
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
</div>