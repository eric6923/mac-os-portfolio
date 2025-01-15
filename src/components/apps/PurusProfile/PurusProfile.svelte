<script lang="ts">
	import { preferences } from '🍎/state/preferences.svelte.ts';
	import BlogIcon from '~icons/mdi/grease-pencil';
	import WorksIcon from '~icons/ic/round-workspaces';
	import EducationIcon from '~icons/mdi/school';
	import BookIcon from '~icons/mdi/book-open';
	import DocumentIcon from '~icons/mdi/file-document';
	import ProjectIcon from '~icons/mdi/laptop';
	import WorkIcon from '~icons/mdi/briefcase';
	import AwardIcon from '~icons/mdi/trophy';
	import SkillIcon from '~icons/mdi/tools';
	import NewsIcon from '~icons/mdi/newspaper';
	import ActivityIcon from '~icons/mdi/account-group';
	let activeSection = 'about';

	const sections = {
		about: { title: 'About', icon: BlogIcon },
		experience: { title: 'Work Experience', icon: WorkIcon },
		education: { title: 'Education', icon: EducationIcon },
		books: { title: 'Published Books', icon: BookIcon },
		articles: { title: 'Featured Articles', icon: DocumentIcon },
		projects: { title: 'Projects', icon: ProjectIcon },
		simulations: { title: 'Virtual Job Simulations', icon: WorksIcon },
		skills: { title: 'Skill Set', icon: SkillIcon },
		media: { title: 'Media Coverage', icon: NewsIcon },
		awards: { title: 'Honors & Awards', icon: AwardIcon },
		activities: { title: 'Extra Curricular', icon: ActivityIcon }
	};
</script>

<section class="container">
	<header class="titlebar app-window-drag-handle">
		<span>Portfolio</span>
	</header>

	<aside class:light={preferences.theme.scheme === 'light'}>
		<nav>
			{#each Object.entries(sections) as [key, { title, icon }]}
				<button 
					class="nav-item" 
					class:active={activeSection === key}
					on:click={() => activeSection = key}
				>
					<svelte:component this={icon} />
					{title}
				</button>
			{/each}
		</nav>
	</aside>

	<section class="content">
		{#if activeSection === 'about'}
			<div class="about-section">
				<img height="200" width="200" src="/purus-profile/profile.webp" alt="Profile picture" />
				<h1>Bhumika Tewari</h1>
				<div class="subtitle">Full Stack Developer • Content Writer • Data Analyst • Cloud Enthusiast</div>
				<p class="bio">
					Passionate technology professional with expertise in full-stack development, 
					data analysis, and cloud computing. Committed to creating impactful solutions 
					and sharing knowledge through technical content writing.
				</p>
			</div>
		<!-- Keep other section content the same -->
		{/if}
	</section>
</section>

<style>
	.container {
		--color: var(--system-color-light-hsl);
		display: grid;
		grid-template-columns: 12rem 1fr;
		grid-template-rows: 3rem 1fr;
		border-radius: inherit;
		background-image: linear-gradient(
			to right,
			hsla(var(--color), 0.7) 12rem,
			hsla(var(--color), 1) 12rem 100%
		);
		transition: --color 200ms ease-in;
		color: var(--system-color-dark);
	}

	.titlebar {
		grid-area: 1 / 1 / span 1 / span 2;
		display: flex;
		justify-content: center;
		z-index: 1;
		padding: 0.9rem 1rem;
		width: 100%;
		border-top-left-radius: inherit;
		border-top-right-radius: inherit;
		user-select: none;
	}

	.titlebar span {
		color: hsla(var(--system-color-dark-hsl), 0.8);
		font-weight: 500;
		font-size: 0.9rem;
		letter-spacing: 0.5px;
	}

	aside {
		grid-area: 1 / 1 / span 2 / span 1;
		transform: translateZ(0);
		height: calc(100% - 2.7px);
		width: calc(12rem - 2.27px);
		margin: 1.8px 0 0px 1.8px;
		border-top-left-radius: 0.5rem;
		border-bottom-left-radius: inherit;
	}

	aside::before {
		content: '';
		width: inherit;
		height: inherit;
		border-radius: inherit;
		position: fixed;
		left: 0;
		top: 0;
		z-index: -1;
		backdrop-filter: blur(12px);
	}

	aside.light {
		height: calc(100% - 3px);
		width: calc(12rem - 2.5px);
		margin: 1.7px 0 0px 1.7px;
		border-top-left-radius: 0.5rem;
		border-bottom-left-radius: 0.5rem;
	}

	nav {
		display: flex;
		flex-direction: column;
		gap: 0.2rem;
		margin: 4rem 0.6rem;
	}

	.nav-item {
    display: grid;
    grid-template-columns: 1.5rem 1fr;  /* Fixed width for icon column */
    align-items: center;
    color: hsla(var(--system-color-dark-hsl), 0.9);
    text-decoration: none;
    font-weight: 400;
    padding: 0.5rem 0.5rem;
    border-radius: 0.4rem;
    transition: background-color 100ms ease;
    border: none;
    background: none;
    width: 100%;
    text-align: left;
    cursor: pointer;
}

/* Add styles for the icon component */
.nav-item :global(svg) {
    width: 1.2rem;
    height: 1.2rem;
}

	.nav-item:hover {
		background-color: hsla(var(--system-color-dark-hsl), 0.2);
	}

	.nav-item.active {
		background-color: hsla(var(--system-color-dark-hsl), 0.2);
	}

	.content {
		grid-area: 2 / 2 / span 1 / span 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 1rem;
	}

	/* About section styles */
	.about-section {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		max-width: 42rem;
		margin: 0 auto;
	}

	img {
		border-radius: 50%;
		margin-bottom: 1.5rem;
	}

	h1 {
		font-size: 2.618rem;
		line-height: 1.618;
		margin-bottom: 0.5rem;
	}

	.subtitle {
		font-size: 1.0rem;
		color: hsla(var(--system-color-dark-hsl), 0.8);
		margin-bottom: 1.5rem;
	}

	.bio {
		line-height: 1.618rem;
	}

	/* Keep other content styles the same */
</style>