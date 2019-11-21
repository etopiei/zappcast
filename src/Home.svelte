<script>
	let email = "";
	let subscribed = false;
	const subscribe = () => {
		fetch("https://75ehnbqn9b.execute-api.ap-southeast-2.amazonaws.com/default/writeEmailToDB", {method: "POST", mode: "no-cors", body: JSON.stringify({"email": email})});
		email = "";
		subscribed = true;
	};
</script>

<style>
	.main {
		margin-left: 10%;
		margin-right: 10%;
	}
	.subbed {
		background-color: #d0ffd0;
	}
	img {
		width: 200px;
	}
	p {
		padding: 8px;
		margin: 0;
	}
</style>

<div class="main">
	<p>ZappCast is a programming podcast coming soon <br> ... <br> If you are interested in programming, banter, and the tech industry then this may just be the podcast for you.</p>
	<p>Look out for our logo wherever you get your podcasts! </p>
	<img src="logo.png" alt="logo">
	<h4> Enter your email to be notified when we get started! *</h4>
	{#if !subscribed}
		<form>
			<input placeholder="Email" bind:value={email}/>
			<button on:click={() => subscribe()}>Submit</button>
		</form>
	{:else}
		<p class="subbed"> You have been subscribed! </p>
	{/if}
	<p> *By signing up to receive this email notification you are also permitting us to email you any advertising offers that may or may not interest you.</p>
	<p> Totally kidding, we'll only email you once the first episode is out. </p>
</div>