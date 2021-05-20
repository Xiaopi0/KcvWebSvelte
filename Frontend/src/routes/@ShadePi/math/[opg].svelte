<script context="module">
	export async function preload(page, session) {
		const { opg } = page.params;

		const res = await this.fetch(`@ShadePi/math/${opg}.json`);
		const Opg = await res.json();

		return { Opg};
	}
</script>

<script>
	export let Opg;
</script>

<svelte:head>
	<title>Opg</title>
</svelte:head>

<h1>Opg</h1>

<div class='content'>
	{Opg}
</div>