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
	import { onMount } from 'svelte';

	const setOpgClassName = (_Opg) => {
		const OpgName = _Opg.opgname
		const className = classNames({'StartOpg': OpgName.endsWith('a') || OpgName.endsWith('1')}, `${OpgName.replace(".", "_")}`, 'opg')
		return className;
	}

	const checkClassName = (_Opg) => {
		const OpgName = _Opg.opgname

		if(OpgName.endsWith('a') || OpgName.endsWith('1')) {
			return true
		} else {
			return false
		}
	}
</script>

<style>
	.opgs {
		font-family: 'Times New Roman';
		text-align: center;
	}

	#mainTitle {
		font-weight: bold;
	}
</style>

<svelte:head>
	<title>{opg}</title>
</svelte:head>


<div class="opgs">
	<h1 id="mainTitle">{opg}</h1>
	{#each Opgs as Opg}
		<span class={setOpgClassName(Opg)} id={Opg.opgname.replace(".", "_")}>
			{#if checkClassName(Opg)}
				<h1>{ Opg.opgname }</h1><br/>
			{:else}
				<h2>{ Opg.opgname }</h2><br/>
			{/if}
			<p>{ Opg.result }</p><br/><br/><br/>
		</span>
	{/each}
</div>