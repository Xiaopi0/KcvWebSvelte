<script>
import { text } from "svelte/internal";

async function toOpg(event) {
    console.log(event.target.selectedOpg.value)
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
    <h1 class="Title" id="MainTitle">@ShadePi/math/index.svelte</h1><br />
    <form class="opgForm" id="opgSelector" on:submit|preventDefault="{toOpg}">
        <input type="text" name="selectedOpg" placeholder="Opg name eg. FP9_03_12_2019" id="selectedOpg"/>
    </form>
</div>