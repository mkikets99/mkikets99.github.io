<script lang="ts">
	import { onMount } from 'svelte';
	import { 
		ExternalLink, 
		Code2, 
		Layers, 
		Database, 
		Cloud, 
		Terminal, 
		Cpu, 
		Globe, 
		Server,
		Briefcase,
		Calendar
	} from 'lucide-svelte';
	import GithubIcon from '$lib/components/GithubIcon.svelte';

	// Data
	const projects = [
		{ name: 'Project 1', description: 'A brief description of this cool project and what it does.', link: 'https://github.com/mkikets99', icon: Globe, tags: [{ name: 'SvelteKit', icon: Code2 }, { name: 'Skeleton', icon: Layers }, { name: 'TypeScript', icon: Terminal }] },
		{ name: 'Project 2', description: 'Another amazing project demonstrating skills in various technologies.', link: 'https://github.com/mkikets99', icon: Database, tags: [{ name: 'Go', icon: Server }, { name: 'React', icon: Globe }, { name: 'Docker', icon: Cloud }] },
		{ name: 'Project 3', description: 'A third project highlighting problem-solving and architectural design.', link: 'https://github.com/mkikets99', icon: Cpu, tags: [{ name: 'Python', icon: Terminal }, { name: 'FastAPI', icon: Server }, { name: 'AWS', icon: Cloud }] }
	];

	const experience = [
		{ role: 'Senior Software Engineer', company: 'Innovative Tech Inc.', period: '2022 - Present', description: 'Leading development of high-scale cloud applications and mentoring junior developers.' },
		{ role: 'Software Developer', company: 'Growth Startups', period: '2019 - 2022', description: 'Full-stack development using React and Node.js to build user-facing products.' }
	];

	const skills = [
		{ name: 'Svelte', icon: Code2 }, { name: 'TypeScript', icon: Terminal }, { name: 'Node.js', icon: Server }, { name: 'Go', icon: Cpu }, { name: 'AWS', icon: Cloud }, { name: 'Docker', icon: Layers }, { name: 'Kubernetes', icon: Globe }, { name: 'CI/CD', icon: Briefcase }
	];

	// Intersection Observer Logic
	let visibleSections = $state(new Set());

	onMount(() => {
		const observer = new IntersectionObserver((entries) => {
			entries.forEach(entry => {
				if (entry.isIntersecting) {
					visibleSections.add(entry.target.id);
				} else {
					// Optional: remove if you want them to re-animate when scrolling back
					// visibleSections.delete(entry.target.id);
				}
				visibleSections = new Set(visibleSections); // Trigger reactivity
			});
		}, { threshold: 0.2 });

		document.querySelectorAll('section').forEach(section => observer.observe(section));
		return () => observer.disconnect();
	});

	function isVisible(id: string) {
		return visibleSections.has(id);
	}
</script>

<!-- HERO SECTION -->
<section id="hero" class="h-screen w-full snap-start flex items-center justify-center p-8 transition-all duration-1000 ease-out {isVisible('hero') ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}">
	<div class="max-w-4xl text-center space-y-6">
		<h1 class="text-6xl md:text-9xl font-bold tracking-tighter">Mykola Kikets</h1>
		<p class="text-primary-500 font-mono italic text-xl md:text-2xl opacity-80 uppercase tracking-[0.3em]">
			"when curiosity leads the way"
		</p>
		<p class="text-xl md:text-2xl text-surface-400 max-w-2xl mx-auto pt-8 leading-relaxed">
			Building robust, scalable applications with a focus on quality and performance.
			Passionate about modern web technologies and clean architecture.
		</p>
		<div class="flex justify-center gap-6 pt-12">
			<a href="#projects" class="btn bg-primary-500 hover:bg-primary-600 text-surface-950 font-bold px-10 py-4 rounded-xl flex items-center gap-3 transition-transform hover:scale-105 active:scale-95 shadow-xl shadow-primary-500/20">
				<GithubIcon size={24} /> View Projects
			</a>
			<a href="#about" class="btn border-2 border-surface-700 hover:bg-surface-800 px-10 py-4 rounded-xl font-bold transition-all hover:border-surface-500">
				Learn More
			</a>
		</div>
	</div>
</section>

<!-- ABOUT SECTION -->
<section id="about" class="h-screen w-full snap-start flex items-center justify-center p-8 bg-surface-900/30 transition-all duration-1000 ease-out {isVisible('about') ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}">
	<div class="max-w-6xl w-full grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
		<div class="space-y-8">
			<h2 class="text-4xl md:text-6xl font-bold tracking-tight">About Me</h2>
			<div class="space-y-4 text-lg md:text-xl text-surface-300 leading-relaxed">
				<p>
					I'm a software engineer based in the cloud. My journey started with a curiosity for how things work, which led to a career in building complex digital systems.
				</p>
				<p>
					I specialize in backend development, distributed systems, and modern frontend frameworks like Svelte. When I'm not coding, I'm exploring new technologies.
				</p>
			</div>
			
			<div class="space-y-6 pt-4">
				<h3 class="text-2xl font-bold text-primary-400">Core Expertise</h3>
				<div class="flex flex-wrap gap-3">
					{#each skills as skill}
						{@const Icon = skill.icon}
						<span class="bg-surface-800 px-4 py-2 rounded-xl text-sm border border-surface-700 flex items-center gap-3 hover:border-primary-500 transition-colors">
							<Icon size={18} />
							{skill.name}
						</span>
					{/each}
				</div>
			</div>
		</div>
		
		<div class="flex justify-center relative">
			<div class="relative group">
				<div class="w-64 h-64 md:w-96 md:h-96 rounded-[2rem] border-4 border-primary-500/30 overflow-hidden shadow-2xl relative transition-transform group-hover:scale-[1.02] rotate-3 group-hover:rotate-0 duration-500">
					<img src="https://api.dicebear.com/7.x/avataaars/svg?seed=Mykola" alt="Mykola Kikets" class="w-full h-full object-cover bg-surface-800" />
				</div>
				<div class="absolute -inset-8 bg-primary-500/10 blur-3xl rounded-full -z-10 animate-pulse"></div>
			</div>
		</div>
	</div>
</section>

<!-- PROJECTS SECTION -->
<section id="projects" class="h-screen w-full snap-start flex items-center justify-center p-8 transition-all duration-1000 ease-out {isVisible('projects') ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}">
	<div class="max-w-7xl w-full space-y-12">
		<div class="flex justify-between items-end">
			<h2 class="text-4xl md:text-6xl font-bold tracking-tight">Selected Projects</h2>
			<a href="https://github.com/mkikets99" class="text-primary-400 hover:underline flex items-center gap-2 mb-2 font-mono">View All Projects &rarr;</a>
		</div>
		
		<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
			{#each projects as project}
				{@const ProjectIcon = project.icon}
				<div class="bg-surface-900/50 backdrop-blur-sm border border-surface-800 p-8 rounded-2xl hover:border-primary-500 transition-all flex flex-col justify-between group hover:-translate-y-2 duration-300 shadow-xl">
					<div class="space-y-6">
						<div class="w-14 h-14 rounded-xl bg-primary-500/10 flex items-center justify-center text-primary-500 group-hover:bg-primary-500 group-hover:text-surface-950 transition-all duration-500">
							<ProjectIcon size={32} />
						</div>
						
						<h3 class="text-2xl font-bold flex items-center justify-between">
							{project.name}
							<ExternalLink size={20} class="opacity-0 group-hover:opacity-100 transition-opacity" />
						</h3>
						
						<p class="text-surface-400 text-lg leading-relaxed">{project.description}</p>
						
						<div class="flex flex-wrap gap-4 pt-2">
							{#each project.tags as tag}
								{@const TagIcon = tag.icon}
								<span class="text-xs text-primary-400 uppercase tracking-widest font-bold flex items-center gap-2">
									<TagIcon size={14} />
									{tag.name}
								</span>
							{/each}
						</div>
					</div>
					
					<a href={project.link} target="_blank" rel="noreferrer" class="mt-10 btn border border-surface-700 hover:bg-surface-800 hover:border-surface-500 w-full py-3.5 rounded-xl text-center font-bold flex items-center justify-center gap-2 transition-all">
						<GithubIcon size={20} /> Repository
					</a>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- EXPERIENCE SECTION -->
<section id="experience" class="h-screen w-full snap-start flex items-center justify-center p-8 bg-surface-900/30 transition-all duration-1000 ease-out {isVisible('experience') ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}">
	<div class="max-w-5xl w-full space-y-16">
		<div class="flex items-center gap-6">
			<div class="p-4 bg-primary-500/10 rounded-2xl text-primary-500">
				<Briefcase size={40} />
			</div>
			<h2 class="text-4xl md:text-6xl font-bold tracking-tight">Work Experience</h2>
		</div>
		
		<div class="space-y-12">
			{#each experience as exp}
				<div class="flex flex-col md:flex-row md:items-start gap-8 md:gap-16 border-l-4 border-surface-800 pl-12 relative group">
					<div class="absolute w-6 h-6 bg-surface-950 border-4 border-primary-500 rounded-full -left-[15px] top-2 transition-transform group-hover:scale-125 duration-300"></div>
					
					<div class="md:w-1/3 space-y-2">
						<div class="flex items-center gap-3 text-primary-400 font-mono text-lg font-bold">
							<Calendar size={18} />
							<span>{exp.period}</span>
						</div>
						<h4 class="text-2xl font-bold text-surface-200">{exp.company}</h4>
					</div>
					
					<div class="md:w-2/3 space-y-4">
						<h3 class="text-3xl font-bold">{exp.role}</h3>
						<p class="text-surface-400 text-xl leading-relaxed">{exp.description}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	section {
		/* Ensures section takes full height minus potential offset if needed, 
		   but h-screen with snap-start is standard for modular pages */
		will-change: transform, opacity;
	}

	:global(html) {
		scroll-padding-top: 80px; /* Offset for the fixed header */
	}
</style>
