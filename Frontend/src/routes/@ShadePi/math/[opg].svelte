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
	.opgs {
		font-family: 'Times New Roman';
		text-align: center;
	}
</style>

<svelte:head>
	<title>{opg}</title>
</svelte:head>


<div class="opgs">
	<h1>{opg}</h1>
	{#each Opgs as Opg}
		<span class="opg" id={Opg.opgname}>
			<h2>{ Opg.opgname }</h2><br/>
			<p>{ Opg.result }</p><br/><br/><br/>
		</span>
	{/each}
</div>