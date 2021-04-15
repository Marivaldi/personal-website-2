<script>
    import { fly } from "svelte/transition";
    import ProjectsContainer from "./ProjectsContainer.svelte";
    import Project from "./Project.svelte";
    import projects from "../site-data/projects";
    export let closeClicked = () => {};
    console.log(projects);
</script>

<div in:fly={{ y: 650, duration: 2500 }} class="title-text center">
    <!-- svelte-ignore a11y-missing-attribute -->
    <!-- svelte-ignore a11y-missing-content -->
    <a class="close" on:click={closeClicked} />
    <p class="name">Projects</p>
    <p class="tagline">
        Whether I made it through or burned out, these are the projects that I worked
        on in my free time.
    </p>
    <ProjectsContainer>
        {#each projects as project}
            <Project
                title={project.title}
                description={project.description}
                linkToDemo={project.linkToDemo}
                linkToSourceCode={project.linkToSourceCode}
            />
        {/each}
    </ProjectsContainer>
</div>

<style>
    .title-text {
        color: #dbd19a;
        padding-top: 5%;
    }

    p.name {
        font-family: "Libre Baskerville", serif;
        font-size: 4rem;
        font-weight: lighter;
    }

    p.tagline {
        color: #dbd19ad7;
        font-family: "Barlow", sans-serif;
        font-size: 1.6rem;
        padding-top: 2%;
        margin-left: 2%;
        margin-right: 2%;
    }

    .center {
        text-align: center;
    }

    .close {
        position: absolute;
        right: 32px;
        top: 32px;
        width: 32px;
        height: 32px;
        opacity: 0.5;
    }
    .close:hover {
        opacity: 1;
    }
    .close:before,
    .close:after {
        position: absolute;
        left: 15px;
        content: " ";
        height: 33px;
        width: 2px;
        background-color: #dbd19a;
    }
    .close:before {
        transform: rotate(45deg);
    }
    .close:after {
        transform: rotate(-45deg);
    }
</style>
