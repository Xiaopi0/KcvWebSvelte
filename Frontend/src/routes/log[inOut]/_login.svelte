<script>
let email;

async function login(event) {
    alert(event.target.Email.value)
}
</script>

<style>
    .loginFormContainer, .loginForm {
        font-family: 'Times New Roman';
    }

    .formItem {
        max-width: 30%;
    }
</style>

<div class="loginFormContainer">
    <form class="loginForm" id="LoginForm" on:submit|preventDefault="{login()}">
        <input class="formItem" type="text" name="Fornavn" placeholder="Fornavn" id="Fornavn" /><br/>
        <input class="formItem" type="text" name="Efternavn" placeholder="Efternavn" id="Efternavn" /><br/>
        <input class="formItem" type="text" name="Email" placeholder="Email" id="Email" /><br/>
        <input class="formItem" type="password" name="Password" placeholder="Password" id="Password" /><br/>
        <input class="formItem" type="password" name="Confirm_Password" placeholder="Confirm Password" id="Confirm_Password" /><br/>
    </form>
    <pre>
        {#if email}
            {email}
        {/if}
    </pre>
</div>