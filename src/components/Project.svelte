<script>
    import SocialIcon from "./SocialIcon.svelte";
    export let title = "";
    export let description = "";
    export let linkToSourceCode = "";
    export let linkToDemo = "";
</script>

<div class="project">
    <h1>{title}</h1>
    <p class="description">{description}</p>
    {#if linkToDemo !== ""}
        <SocialIcon
            linkToSocial={linkToDemo}
            fontAwesomeClass="fas fa-desktop"
            linkText="Demo"
        />
    {/if}

    <SocialIcon
        linkToSocial={linkToSourceCode}
        fontAwesomeClass="fas fa-code"
        linkText="Code"
    />
</div>

<style>
    .project {
        width: 95%;
        margin: 0 auto;
        padding: 50px;
        text-align: left;
    }

    .project h1 {
        font-family: "Libre Baskerville", serif;
        font-size: 1.5rem;
    }

    .project .description {
        color: #dbd19ad7;
        font-family: "Barlow", sans-serif;
        font-size: 1.3rem;
        padding-bottom: 15px;
    }

    @media (min-width: 768px) {
        .project {
            width: 48%;
        }
    }

    @media (min-width: 992px) {
        .project {
            width: 29%;
        }
    }
</style>
