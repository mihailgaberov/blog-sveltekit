<!-- <script context="module">
  export const load = async () => {
		const ReadMeFile = await import('../../README.md');
    const ReadMe = ReadMeFile.default;

		return {
			props: {
				ReadMe
			}
		}
	}
</script>

<script>
  export let ReadMe
</script> -->


<svelte:head>
	<title>Personal blog by Mihail Gaberov.</title>
</svelte:head>

<h1><img class="head-photo" src="https://mihail-gaberov.eu/static/profile-pic-538ec3f11211b7561f61b99ab54fb65f.jpg" alt="Mihail Gaberov" title="Mihail Gaberov" />Hi, I'm Mihail.</h1>
<!-- <svelte:component this={ReadMe} /> -->
<!-- This is the README.md file in the root of the repo. It serves double duty as the homepage's content. If you'd rather use your own HTML and/or Svelte, you can delete/modify everything above this line. -->