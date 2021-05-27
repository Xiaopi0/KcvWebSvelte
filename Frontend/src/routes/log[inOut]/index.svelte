<script context="module">
	export async function preload(page, session) {
		const { inOut } = page.params;

		return { inOut };
	}
</script>

<script>
    export let inOut

    import Login from './_login.svelte'
    import Logout from "./_logout.svelte";
</script>

<style>
    .pageHolder {
        font-family: 'Times New Roman';
        text-align: center;
    }
</style>

<div class="pageHolder" id="Main">
    {#if inOut == 'in'}
        <span>
            <h1>Login</h1>
            <Login></Login>
        </span>
    {:else if inOut == 'out'}
        <span>
            <h1>Logout</h1>
            <Logout></Logout>
        </span>
    {:else}
        <span>
            <h1>Bad Request - Invalid Syntax</h1>
        </span>
    {/if}
</div>