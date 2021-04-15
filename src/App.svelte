<script>
	let name = "Shayne Moore";
	let visible = false;

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

	setTimeout(() => {
		visible = true;
	}, 200);
</script>

<div class="title-text center">
	<p class="name" in:typewriter={{ speed: 100 }}>{name}</p>
	<p class="occupation">
		Software Engineer II
	</p>
	{#if visible}
		<p class="years-of-experience" in:typewriter={{ speed: 85}}>
			{yearsOfExperience} years of experience
		</p>
	{/if}

	<a href="https://github.com/Marivaldi" class="icon">
		<i class="fab fa-github" />
		<div class="icon-text">GitHub</div>
	</a>
	<a href="/" class="icon">
		<i class="fas fa-atom" />
		<div class="icon-text">Projects</div>
	</a>
	<a href="https://www.linkedin.com/in/shayne-moore/" class="icon">
		<i class="fab fa-linkedin-in" />
		<div class="icon-text">LinkedIn</div>
	</a>
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
</style>
