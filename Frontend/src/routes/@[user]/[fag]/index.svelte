<script context="module">
	export async function preload(page, session) {
		const { user, fag } = page.params;

		return { user, fag };
	}
</script>

<script>
export let fag
export let user

import { text } from "svelte/internal";

async function toOpg(event) {
    const opgId = event.target.selectedOpg.value;
    console.log(opgId)
    const href = window.location.href;
    console.log(href)
    let newHref;
    if(href.endsWith('/')) {
        newHref = href + opgId;
    } else {
        newHref = href + '/' + opgId;
    }
    console.log(newHref)
    try {
       window.location.replace(newHref)
    } catch (error) {
        console.log(error)
    }
}
</script>

<style>
    h1.Title#MainTitle {
        font-family: 'Times New Roman';
    }

    .Container {
        text-align: center;
    }

    #selectedOpg {
        min-width: 200px;
    }
</style>

<svelte:head>
    <title>Opgs</title>
</svelte:head>

<div class="Container">
    <h1 class="Title" id="MainTitle">{`@${user}/${fag}/index.svelte` }</h1><br />
    <form class="opgForm" id="opgSelector" on:submit|preventDefault="{toOpg}">
        <input type="text" name="selectedOpg" placeholder="Opg name fx. FP9_03_12_2019" id="selectedOpg"/>
    </form>
</div>