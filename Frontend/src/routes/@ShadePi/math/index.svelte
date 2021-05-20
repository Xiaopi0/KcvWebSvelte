<script>
    const axios = require('axios');

    function getOpg() {  
        
        axios.get('https://3003-turquoise-mammal-mphszaam.ws-eu04.gitpod.io/opg/FP9_03_12_2019.json')
        .then(function (response) {
          // handle success
          console.log(response);
          console.log(response.data);
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    }
</script>

<style>
    h1.Title#MainTitle {
        font-family: 'Times New Roman';
    }

    .Container {
        display: flex;
        justify-content: center;
    }
</style>

<div class="Container">
    <h1 class="Title" id="MainTitle">@ShadePi/math/index.svelte</h1><br />
    <button on:click={getOpg()} >Click Me</button>
</div>