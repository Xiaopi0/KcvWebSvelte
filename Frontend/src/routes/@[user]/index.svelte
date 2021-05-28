<script context="module">
	export async function preload(page, session) {
		const { user } = page.params;

		return { user };
	}
</script>

<script>
    export let user
</script>

<h1>Hi { user }!</h1>