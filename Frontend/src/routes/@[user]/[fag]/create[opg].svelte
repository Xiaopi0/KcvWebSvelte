<script context="module">
    export async function preload(page, session) {
		const { user, fag, opg  } = page.params;

		return { user, fag, opg };
	}
</script>

<script >
    export let user
    export let fag
    export let opg

    //TinyMCE not working, research
    const tinymce = require('tinymce')

    tinymce.init({
      selector: 'textarea',
      plugins: 'advlist autolink lists link image charmap print preview hr anchor pagebreak',
      toolbar_mode: 'floating',
   });
</script>

<h1>{ user/fag/opg }</h1>

<textarea></textarea>