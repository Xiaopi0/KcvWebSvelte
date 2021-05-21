<script context="module">
	export async function preload(page, session) {
		const { opg } = page.params;

		const res = await this.fetch(`@ShadePi/math/${opg}.json`);
		const Opgs = await res.json();

		return { Opgs, opg };
	}
</script>

<script>
	export let Opgs;
	export let opg;
</script>

<svelte:head>
	<title>{opg}</title>
</svelte:head>

<h1>{opg}</h1>

<div>
	{#each Opgs as Opg}
		<span>
			<h1>{ Opg.opgname }</h1><br/>
			<p>{ Opg.result }</p><br/><br/><br/>
		</span>
	{/each}
</div>