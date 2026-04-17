<script lang="ts">
	import { 
		Github, 
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

	const projects = [
		{
			name: 'Project 1',
			description: 'A brief description of this cool project and what it does.',
			link: 'https://github.com/mkikets99',
			icon: Globe,
			tags: [
				{ name: 'SvelteKit', icon: Code2 },
				{ name: 'Skeleton', icon: Layers },
				{ name: 'TypeScript', icon: Terminal }
			]
		},
		{
			name: 'Project 2',
			description: 'Another amazing project demonstrating skills in various technologies.',
			link: 'https://github.com/mkikets99',
			icon: Database,
			tags: [
				{ name: 'Go', icon: Server },
				{ name: 'React', icon: Globe },
				{ name: 'Docker', icon: Cloud }
			]
		},
		{
			name: 'Project 3',
			description: 'A third project highlighting problem-solving and architectural design.',
			link: 'https://github.com/mkikets99',
			icon: Cpu,
			tags: [
				{ name: 'Python', icon: Terminal },
				{ name: 'FastAPI', icon: Server },
				{ name: 'AWS', icon: Cloud }
			]
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

	const skills = [
		{ name: 'Svelte', icon: Code2 },
		{ name: 'TypeScript', icon: Terminal },
		{ name: 'Node.js', icon: Server },
		{ name: 'Go', icon: Cpu },
		{ name: 'AWS', icon: Cloud },
		{ name: 'Docker', icon: Layers },
		{ name: 'Kubernetes', icon: Globe },
		{ name: 'CI/CD', icon: Briefcase }
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
		<a href="#projects" class="btn bg-primary-500 hover:bg-primary-600 text-surface-950 font-bold px-8 py-3 rounded-lg flex items-center gap-2">
			<Github size={20} /> View Projects
		</a>
		<a href="mailto:contact@example.com" class="btn border border-surface-700 hover:bg-surface-800 px-8 py-3 rounded-lg">
			Contact Me
		</a>
	</div>
</section>

<hr class="opacity-10" />

<!-- About Section -->
<section id="about" class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center py-10">
	<div class="space-y-6 order-2 md:order-1">
		<h2 class="text-3xl font-bold">About Me</h2>
		<p>
			I'm a software engineer based in the cloud. My journey started with a curiosity for how things work, which led to a career in building complex digital systems. I specialize in backend development, distributed systems, and modern frontend frameworks like Svelte.
		</p>
		<p>
			When I'm not coding, you can find me exploring new technologies or contributing to open-source projects.
		</p>
		
		<div class="space-y-4 pt-4">
			<h3 class="text-xl font-bold">Core Skills</h3>
			<div class="flex flex-wrap gap-3">
				{#each skills as skill}
					<span class="bg-surface-800 px-3 py-1.5 rounded-full text-sm border border-surface-700 flex items-center gap-2">
						<svelte:component this={skill.icon} size={14} />
						{skill.name}
					</span>
				{/each}
			</div>
		</div>
	</div>
	
	<!-- Profile Photo Container -->
	<div class="flex justify-center order-1 md:order-2">
		<div class="relative group">
			<!-- Round Photo Placeholder -->
			<div class="w-64 h-64 md:w-80 md:h-80 rounded-full border-4 border-primary-500/30 overflow-hidden shadow-2xl relative transition-transform group-hover:scale-[1.02]">
				<!-- Replace src with your actual photo URL -->
				<img 
					src="https://api.dicebear.com/7.x/avataaars/svg?seed=M" 
					alt="M. Kikets" 
					class="w-full h-full object-cover bg-surface-800"
				/>
				<!-- Decorative Ring -->
				<div class="absolute inset-0 border-2 border-primary-500 rounded-full opacity-0 group-hover:opacity-100 transition-opacity"></div>
			</div>
			<!-- Background Glow -->
			<div class="absolute -inset-4 bg-primary-500/20 blur-3xl rounded-full -z-10 animate-pulse"></div>
		</div>
	</div>
</section>

<!-- Projects Section -->
<section id="projects" class="space-y-8 py-10">
	<h2 class="text-3xl font-bold">Selected Projects</h2>
	<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
		{#each projects as project}
			<div class="bg-surface-900 border border-surface-800 p-6 rounded-xl hover:border-primary-500 transition-all flex flex-col justify-between group">
				<div class="space-y-4">
					<!-- Project Icon/Image Placeholder -->
					<div class="w-12 h-12 rounded-lg bg-primary-500/10 flex items-center justify-center text-primary-500 mb-2 group-hover:bg-primary-500 group-hover:text-surface-950 transition-colors">
						<svelte:component this={project.icon} size={28} />
					</div>
					
					<h3 class="text-xl font-bold flex items-center justify-between">
						{project.name}
						<ExternalLink size={16} class="opacity-0 group-hover:opacity-100 transition-opacity" />
					</h3>
					
					<p class="text-surface-400">{project.description}</p>
					
					<div class="flex flex-wrap gap-3">
						{#each project.tags as tag}
							<span class="text-xs text-primary-400 uppercase tracking-wider font-semibold flex items-center gap-1.5">
								<svelte:component this={tag.icon} size={12} />
								{tag.name}
							</span>
						{/each}
					</div>
				</div>
				
				<a href={project.link} target="_blank" rel="noreferrer" class="mt-8 btn bg-surface-800 hover:bg-surface-700 w-full py-2.5 rounded text-center font-medium flex items-center justify-center gap-2">
					<Github size={18} /> View Repository
				</a>
			</div>
		{/each}
	</div>
</section>

<!-- Experience Section -->
<section id="experience" class="space-y-8 py-10">
	<div class="flex items-center gap-3">
		<Briefcase class="text-primary-500" />
		<h2 class="text-3xl font-bold">Professional Experience</h2>
	</div>
	
	<div class="space-y-12">
		{#each experience as exp}
			<div class="flex flex-col md:flex-row md:items-start gap-4 md:gap-12 border-l-2 border-surface-800 pl-8 relative">
				<div class="absolute w-4 h-4 bg-primary-500 rounded-full -left-[9px] top-1 shadow-[0_0_10px_rgba(var(--color-primary-500),0.5)]"></div>
				
				<div class="md:w-1/4 flex items-center gap-2 text-surface-400 font-mono">
					<Calendar size={14} />
					<span>{exp.period}</span>
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
