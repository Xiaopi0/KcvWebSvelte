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

<style>
	.opg {
		font-family: 'Times New Roman';
	}
</style>

<svelte:head>
	<title>{opg}</title>
</svelte:head>

<h1>{opg}</h1>

<div>
	{#each Opgs as Opg}
		<span class="opg" id={Opg.opgname}>
			<h2>{ Opg.opgname }</h2><br/>
			<p>{ Opg.result }</p><br/><br/><br/>
		</span>
	{/each}
</div>