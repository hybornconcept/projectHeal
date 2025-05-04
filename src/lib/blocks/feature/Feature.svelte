<!--
	Installed from github/SikandarJODD/cnblocks
-->

<script lang="ts">
	import { onMount } from 'svelte';
	
	const benefits = [
		{
			id: 1,
			name: 'Health Coverage',
			description: 'Premium Benefits'
		},
		{
			id: 2,
			name: 'Free Education',
			description: 'Free Masterclass for all'
		},
		{
			id: 3,
			name: 'Good Salary',
			description: 'Starting at $100K'
		},
		{
			id: 4,
			name: 'Innovation',
			description: 'Use Creative Ideas'
		},
		{
			id: 5,
			name: 'Remote Work',
			description: 'Work from anywhere'
		},
		{
			id: 6,
			name: 'Career Growth',
			description: 'Fast-track promotions'
		},
		{
			id: 6,
			name: 'Career Growth',
			description: 'Fast-track promotions'
		},
		{
			id: 6,
			name: 'Career Growth',
			description: 'Fast-track promotions'
		}
	
	];
	
	let currentSlide = 0;
	const slidesPerView = 4;
	const totalSlides = Math.ceil(benefits.length / slidesPerView);
	
	function nextSlide() {
		currentSlide = (currentSlide + 1) % totalSlides;
	}
	
	function prevSlide() {
		currentSlide = (currentSlide - 1 + totalSlides) % totalSlides;
	}
	
	function goToSlide(index: number) {
		currentSlide = index;
	}
	
	// Auto-advance slides
	onMount(() => {
		const interval = setInterval(() => {
			nextSlide();
		}, 5000);
		
		return () => clearInterval(interval);
	});
</script>

<div class="relative w-full bg-blue-600 py-6 md:py-12 rounded-[10px] max-w-6xl mx-auto ">
	<div class="mx-auto max-w-6xl px-12">
		<!-- Title section -->
		<div class="mb-6 text-white">
			<h2 class="text-3xl font-bold">Employee Perks &</h2>
			<h2 class="text-3xl font-bold">Benefits</h2>
		</div>

		<!-- Benefits cards carousel -->
		<div class="relative">
			<div class="overflow-hidden">
				<div 
					class="flex transition-transform duration-500 ease-in-out" 
					style="transform: translateX(-{currentSlide * 100}%);"
				>
					{#each benefits as benefit}
						<div class="w-full sm:w-1/2 md:w-1/4 flex-shrink-0 p-3">
							<div class="bg-blue-500/40 backdrop-blur-sm p-6 rounded-xl border border-blue-400/30 h-full">
								<div class="mb-4 flex items-center justify-between">
									<span class="flex h-8 w-8 items-center justify-center rounded-full border border-blue-300 text-xs font-medium text-white">{benefit.id}</span>
								</div>
								<h3 class="font-semibold text-white text-lg">{benefit.name}</h3>
								<p class="text-sm text-blue-100">{benefit.description}</p>
							</div>
						</div>
					{/each}
				</div>
			</div>
		</div>

		<!-- Navigation and progress container -->
		<div class="mt-8 flex justify-between items-center">
			<!-- Navigation buttons - moved to bottom left -->
			<div class="flex gap-2">
				<button 
					class="bg-blue-500/40 backdrop-blur-sm rounded-lg p-3 text-white border border-blue-400/30"
					on:click={prevSlide}
				>
					←
				</button>
				<button 
					class="bg-blue-500/40 backdrop-blur-sm rounded-lg p-3 text-white border border-blue-400/30"
					on:click={nextSlide}
				>
					→
				</button>
			</div>
			
			<!-- Progress indicators - moved to bottom right -->
			<div class="flex gap-2">
				{#each Array(totalSlides) as _, i}
					<button 
						class="h-0.5 w-8 {i === currentSlide ? 'bg-white' : 'bg-blue-400/30'}"
						on:click={() => goToSlide(i)}
						aria-label="Go to slide {i+1}"
					></button>
				{/each}
			</div>
		</div>
	</div>
</div>





