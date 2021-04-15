<script>
	import LandingPage from "./components/LandingPage.svelte";
	import ProjectsPage from "./components/ProjectsPage.svelte";

	let showProjects = false;

	function openProjects() {
		showProjects = true;
	}

	function closeProjects() {
		showProjects = false;
	}
</script>

{#if !showProjects}
	<LandingPage projectsClicked={openProjects} />
{/if}

{#if showProjects}
	<ProjectsPage closeClicked={closeProjects} />
{/if}
