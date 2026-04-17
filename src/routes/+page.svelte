<script lang="ts">
	const projects = [
		{
			name: 'Project 1',
			description: 'A brief description of this cool project and what it does.',
			link: 'https://github.com/mkikets99',
			tags: ['SvelteKit', 'Skeleton', 'TypeScript']
		},
		{
			name: 'Project 2',
			description: 'Another amazing project demonstrating skills in various technologies.',
			link: 'https://github.com/mkikets99',
			tags: ['Go', 'React', 'Docker']
		},
		{
			name: 'Project 3',
			description: 'A third project highlighting problem-solving and architectural design.',
			link: 'https://github.com/mkikets99',
			tags: ['Python', 'FastAPI', 'AWS']
		}
	];

	const experience = [
		{
			role: 'Senior Software Engineer',
			company: 'Innovative Tech Inc.',
			period: '2022 - Present',
			description: 'Leading development of high-scale cloud applications and mentoring junior developers.'
		},
		{
			role: 'Software Developer',
			company: 'Growth Startups',
			period: '2019 - 2022',
			description: 'Full-stack development using React and Node.js to build user-facing products.'
		}
	];
</script>

<!-- Hero Section -->
<section class="text-center py-20 space-y-6">
	<h1 class="text-5xl md:text-7xl font-bold">Software Engineer</h1>
	<p class="text-xl text-surface-400 max-w-2xl mx-auto">
		Building robust, scalable applications with a focus on quality and performance.
		Passionate about modern web technologies and clean architecture.
	</p>
	<div class="flex justify-center gap-4">
		<a href="#projects" class="btn bg-primary-500 hover:bg-primary-600 text-surface-950 font-bold px-8 py-3 rounded-lg">
			View Projects
		</a>
		<a href="mailto:contact@example.com" class="btn border border-surface-700 hover:bg-surface-800 px-8 py-3 rounded-lg">
			Contact Me
		</a>
	</div>
</section>

<hr class="opacity-10" />

<!-- About Section -->
<section id="about" class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center py-10">
	<div class="space-y-6">
		<h2 class="text-3xl font-bold">About Me</h2>
		<p>
			I'm a software engineer based in the cloud. My journey started with a curiosity for how things work, which led to a career in building complex digital systems. I specialize in backend development, distributed systems, and modern frontend frameworks like Svelte.
		</p>
		<p>
			When I'm not coding, you can find me exploring new technologies or contributing to open-source projects.
		</p>
	</div>
	<div class="bg-surface-900 p-8 rounded-xl shadow-xl space-y-4 border border-surface-800">
		<h3 class="text-xl font-bold">Core Skills</h3>
		<div class="flex flex-wrap gap-2">
			{#each ['Svelte', 'TypeScript', 'Node.js', 'Go', 'AWS', 'Docker', 'Kubernetes', 'CI/CD'] as skill}
				<span class="bg-surface-800 px-3 py-1 rounded-full text-sm border border-surface-700">{skill}</span>
			{/each}
		</div>
	</div>
</section>

<!-- Projects Section -->
<section id="projects" class="space-y-8 py-10">
	<h2 class="text-3xl font-bold">Selected Projects</h2>
	<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
		{#each projects as project}
			<div class="bg-surface-900 border border-surface-800 p-6 rounded-xl hover:border-primary-500 transition-all flex flex-col justify-between">
				<div class="space-y-4">
					<h3 class="text-xl font-bold">{project.name}</h3>
					<p class="text-surface-400">{project.description}</p>
					<div class="flex flex-wrap gap-2">
						{#each project.tags as tag}
							<span class="text-xs text-primary-400 uppercase tracking-wider font-semibold">{tag}</span>
						{/each}
					</div>
				</div>
				<a href={project.link} target="_blank" rel="noreferrer" class="mt-6 btn bg-surface-800 hover:bg-surface-700 w-full py-2 rounded text-center">
					View Repository &rarr;
				</a>
			</div>
		{/each}
	</div>
</section>

<!-- Experience Section -->
<section id="experience" class="space-y-8 py-10">
	<h2 class="text-3xl font-bold">Professional Experience</h2>
	<div class="space-y-12">
		{#each experience as exp}
			<div class="flex flex-col md:flex-row md:items-start gap-4 md:gap-12 border-l-2 border-surface-800 pl-8 relative">
				<div class="absolute w-4 h-4 bg-primary-500 rounded-full -left-[9px] top-1 shadow-[0_0_10px_rgba(var(--color-primary-500),0.5)]"></div>
				<div class="md:w-1/4">
					<p class="text-surface-400 font-mono">{exp.period}</p>
				</div>
				<div class="md:w-3/4 space-y-2">
					<h3 class="text-xl font-bold">{exp.role}</h3>
					<h4 class="text-primary-400 font-semibold">{exp.company}</h4>
					<p class="text-surface-400 leading-relaxed">{exp.description}</p>
				</div>
			</div>
		{/each}
	</div>
</section>
