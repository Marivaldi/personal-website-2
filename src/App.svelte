<script>
	import { fade, fly } from "svelte/transition";
	let name = "Shayne Moore";
	let showWorkExperience = false;
	let showProjects = false;

	function calculateYearsOfExperience() {
		var ageDifMs = Date.now() - new Date("03-06-2016");
		var ageDate = new Date(ageDifMs);
		return Math.abs(ageDate.getUTCFullYear() - 1970);
	}

	let yearsOfExperience = calculateYearsOfExperience();

	function typewriter(node, { speed = 50 }) {
		const valid =
			node.childNodes.length === 1 &&
			node.childNodes[0].nodeType === Node.TEXT_NODE;

		if (!valid) {
			throw new Error(
				`This transition only works on elements with a single text node child`
			);
		}

		const text = node.textContent;
		const duration = text.length * speed;

		return {
			duration,
			tick: (t) => {
				const i = ~~(text.length * t);
				node.textContent = text.slice(0, i);
			},
		};
	}

	function openProjects() {
		showProjects = true;
	}

	function closeProjects() {
		showProjects = false;
	}

	setTimeout(() => {
		showWorkExperience = true;
	}, 200);
</script>

{#if !showProjects}
	<div in:fade="{{duration:500}}" out:fade="{{duration:500}}" class="title-text center">
		<p class="name">{name}</p>
		<p class="occupation">Software Engineer II</p>
		{#if showWorkExperience}
			<p class="years-of-experience" in:typewriter={{ speed: 85 }}>
				{yearsOfExperience} years of experience
			</p>
		{/if}

		<a href="https://github.com/Marivaldi" class="icon grow">
			<i class="fab fa-github" />
			<div class="icon-text">GitHub</div>
		</a>
		<a class="icon grow" on:click={openProjects}>
			<i class="fas fa-atom" />
			<div class="icon-text">Projects</div>
		</a>
		<a href="https://www.linkedin.com/in/shayne-moore/" class="icon grow">
			<i class="fab fa-linkedin-in" />
			<div class="icon-text">LinkedIn</div>
		</a>
	</div>
{/if}

{#if showProjects}
	<div in:fly={{ y: 100, duration: 2500 }} class="title-text center">
		<a class="close" on:click={closeProjects}/>
		<p class="name">Projects</p>
		<p class="tagline">Whether I made it through or burned out, these are the projects I worked on in my free time.</p>
	</div>
{/if}

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

	p.tagline {
		color: #dbd19ad7;
		font-family: "Barlow", sans-serif;
		font-size: 1.6rem;
		padding-top: 2%;
		margin-left: 2%;
		margin-right: 2%;
	}

	p.years-of-experience {
		color: #dbd19ad7;
		font-family: "Barlow", sans-serif;
		font-size: 2.2rem;
		padding-bottom: 2%;
	}

	.icon {
		font-size: 2.2rem;
		padding: 10px;
		display: inline-block;
	}

	.icon-text {
		font-size: 1.3rem;
		font-family: "Barlow", sans-serif;
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
