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

	const classNames = require('classnames');
</script>

<style>
	.opgs {
		font-family: 'Times New Roman';
		text-align: center;
	}

	#mainTitle {
		font-weight: bold;
	}

	.StartOpg {
		color: red;
	}

	.NonStartOpg {
		color: green;
	}
</style>

<svelte:head>
	<title>{opg}</title>
</svelte:head>


<div class="opgs">
	<h1 id="mainTitle">{opg}</h1>
	{#each Opgs as Opg}
		<span class="{classNames({'StartOpg': Opg.opgname.endsWith('a') || Opg.opgname.endsWith('1')}, {'NonStartOpg': !Opg.opgname.endsWith('a') && !Opg.opgname.endsWith('1')}, `${Opg.opgname.replace(".", "_")}`, 'opg')}" id="{Opg.opgname.replace(".", "_")}">
			{#if Opg.opgname.endsWith('a') || Opg.opgname.endsWith('1')}
				<h1>{ Opg.opgname }</h1><br/>
			{:else}
				<h2>{ Opg.opgname }</h2><br/>
			{/if}
			<p>{ Opg.result }</p><br/><br/><br/>
		</span>
	{/each}
</div>