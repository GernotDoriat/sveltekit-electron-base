<script>
	import { browser } from "$app/environment";

	let desktop;

	if (window.electron && browser) {
		window.electron.receive("from-main", (data) => {
			desktop = `Received Message "${data}" from Electron`;
			console.log(desktop);
		});
	}

	const agent = window.electron ? "Electron" : "Browser";
</script>

<main class="bg-blue-200 h-screen">
	<h1 class="text-4xl">Hello {agent}!</h1>
</main>

<style lang="postcss">
	:root {
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
	}

	:global(body) {
		margin: 0;
		padding: 0;
	}

	main {
		padding: 2em 1em 1em 1em;
		text-align: center;
		animation: fade 1s;
		margin: 0 auto;
	}

	@keyframes fade {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}
</style>
