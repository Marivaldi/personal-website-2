<script>
    import { fade } from "svelte/transition";
    import SocialIcon from "./SocialIcon.svelte";
    import typewriter from "../animations/typewriter";
    import {yearsSince} from "../functions/date";

    export let projectsClicked = () => {};

    let showWorkExperience = false;

    let theDateIStartedWorking = new Date("03-06-2016");
    let yearsOfExperience = yearsSince(theDateIStartedWorking);

    setTimeout(() => {
        showWorkExperience = true;
    }, 200);
</script>

<div
    in:fade={{ duration: 500 }}
    out:fade={{ duration: 500 }}
    class="title-text center"
>
    <p class="name">Shayne Moore</p>
    <p class="occupation">Software Engineer II</p>

    {#if showWorkExperience}
        <p class="years-of-experience" in:typewriter={{ speed: 85 }}>
            {yearsOfExperience} years of experience
        </p>
    {/if}

    <SocialIcon
        linkToSocial="https://github.com/Marivaldi"
        fontAwesomeClass="fab fa-github"
        linkText="GitHub"
    />
    <SocialIcon
        fontAwesomeClass="fas fa-atom"
        onClick={projectsClicked}
        linkText="Projects"
    />
    <SocialIcon
        linkToSocial="https://www.linkedin.com/in/shayne-moore/"
        fontAwesomeClass="fab fa-linkedin-in"
        linkText="LinkedIn"
    />
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

    p.occupation {
        color: #dbd19ad7;
        font-family: "Barlow", sans-serif;
        font-size: 2.5rem;
    }

    p.years-of-experience {
        color: #dbd19ad7;
        font-family: "Barlow", sans-serif;
        font-size: 2.2rem;
        padding-bottom: 2%;
    }
</style>
