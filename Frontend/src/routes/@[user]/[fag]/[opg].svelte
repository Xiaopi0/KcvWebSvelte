<script context="module">
	export async function preload(page, session) {
		const { user, fag, opg  } = page.params;

		const res = await this.fetch(`@${user}/${fag}/${opg}.json`);
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
		color: blue;
	}

	.NonStartOpg {
		color: rgb(0, 255, 0);
	}

	#deadline {
		color: red;
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
				<h1 id="opgname">{ Opg.opgname }</h1><br/>
				<h2 id="deadline">Deadline: { Opg.deadline }</h2><br/>
			{:else}
				<h2 id="opgname">{ Opg.opgname }</h2><br/>
			{/if}
			<p id="opg">Opgave: {@html Opg.opg }</p>
			{#if Opg.status != null}
				<p id="status">Status: {@html Opg.status}</p><br/><br/><br/>
			{:else}
				<p id="result">Resultat: {@html Opg.result }</p><br/><br/><br/>
			{/if}
		</span>
	{/each}
</div>