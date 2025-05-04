<script lang="ts">
	import Button from "$lib/components/ui/button/button.svelte";
	
	import Logo from "$lib/components/web/Logo.svelte";
	import { cn } from "$lib/utils";
	import { ArrowRight,Menu,X } from "lucide-svelte";
	import { scrollY } from "svelte/reactivity/window";
	import Marquee from "$lib/components/ui/Marquee/Marquee.svelte";
  
	let menuItems = [
	  { name: "Features", href: "/features" },
	  { name: "Solution", href: "/solution" },
	  { name: "Pricing", href: "/pricing" },
	  { name: "About", href: "/about" },
	];
	let menuState = $state(false);
	let isScrolled = $derived.by(() => {
	  if (scrollY.current !== undefined && scrollY.current > 50) {
		return true;
	  }
	  return false;
	});
  
	export const GRADIENT_ANGLES = {
	  top: 0,
	  right: 90,
	  bottom: 180,
	  left: 270,
	};
  
	type ProgressiveBlurProps = {
	  direction?: keyof typeof GRADIENT_ANGLES;
	  blurLayers?: number;
	  class?: string;
	  blurIntensity?: number;
	};
	
	// Typing effect variables
	const phrases = [
		"at your<br />Convenience.",
		"at your<br />Schedule.",
		"One Click<br />Away.",
		"Appointments<br />Made Simple.",
		"Skip the<br />Wait."
	];
	
	let currentPhraseIndex = $state(0);
	let displayText = $state('');
	let isDeleting = $state(false);
	let isWaiting = $state(false);
	let typingSpeed = $state(100); // milliseconds per character
	let deletingSpeed = $state(50); // faster deletion
	let pauseDelay = $state(2000); // pause at complete phrase
	let cursorVisible = $state(true);
	
	// Cursor blinking effect
	$effect(() => {
		const cursorInterval = setInterval(() => {
			cursorVisible = !cursorVisible;
		}, 500);
		
		return () => clearInterval(cursorInterval);
	});
	
	// Typing effect function
	$effect(() => {
		if (isWaiting) return;
		
		const currentPhrase = phrases[currentPhraseIndex];
		const currentLength = displayText.length;
		
		if (!isDeleting && displayText === currentPhrase) {
			// Finished typing current phrase, pause before deleting
			isWaiting = true;
			setTimeout(() => {
				isDeleting = true;
				isWaiting = false;
			}, pauseDelay);
			return;
		}
		
		if (isDeleting && displayText === '') {
			// Finished deleting, move to next phrase
			isDeleting = false;
			currentPhraseIndex = (currentPhraseIndex + 1) % phrases.length;
			return;
		}
		
		// Set timeout for next character
		const timeout = setTimeout(() => {
			if (isDeleting) {
				// Delete character
				displayText = displayText.substring(0, currentLength - 1);
			} else {
				// Add character
				displayText = currentPhrase.substring(0, currentLength + 1);
			}
		}, isDeleting ? deletingSpeed : typingSpeed);
		
		return () => clearTimeout(timeout);
	});
</script>
  
{@render header()}
<main class="overflow-x-hidden">
	<section>
	  <div class="pb-10 pt-12 md:pb-22 lg:pb-14 lg:pt-44">
		<div class="relative mx-auto flex max-w-6xl flex-row items-center justify-between gap-8 px-6">
		  <div class="w-full text-center lg:text-left lg:w-1/2">
		
				<a
				href="/"
				class="rounded-full ml-0 flex w-fit items-center gap-2 border-2 border-blue-300 dark:border-gray-700 p-1 pr-3 mb-4"
			  >
				<span
				  class="bg-muted rounded-full px-2 py-1 text-xs"
				  >New</span
				>
				<span class="text-sm"> HealNext Beta version 0.0.2</span>
			
	
				<ArrowRight class="size-4" />
			  </a>
		
			
			<h1 class="text-balance text-5xl md:text-6xl xl:text-7xl font-extrabold text-pretty bg-clip-text text-transparent bg-gradient-to-b from-blue-400 to-blue-800 min-h-[8rem] md:min-h-[12rem] xl:min-h-[14rem] transition-all duration-300">
			  Your health<br />{@html displayText}<span class={cursorVisible ? 'opacity-100' : 'opacity-0'}>|</span>
			</h1>
			
			<!-- <div class="mt-6 flex -space-x-4 rtl:space-x-reverse">
			  <img class="h-12 w-12 rounded-full border-2 border-background" src="https://randomuser.me/api/portraits/women/1.jpg" alt="User" />
			  <img class="h-12 w-12 rounded-full border-2 border-background" src="https://randomuser.me/api/portraits/men/1.jpg" alt="User" />
			  <img class="h-12 w-12 rounded-full border-2 border-background" src="https://randomuser.me/api/portraits/women/2.jpg" alt="User" />
			</div> -->

			<p class="mt-2 text-pretty text-lg text-muted-foreground">
				Connecting patients with medical professionals seamlessly. Browse, book, and receive care on your terms
			</p>

			<div class="mt-8 flex items-center justify-center gap-4 sm:flex-row lg:justify-start">
			  <Button href="/appointment" variant="outline" size="lg" class="px-12 py-6 text-base rounded-full border-blue-500 hover:bg-blue-600 hover:text-white hover:border-blue-600 transition-colors duration-300 text-blue-600">
				<span class="text-nowrap">Book an Appointment</span>
			  </Button>
			  <a href="/features" class="text-base font-medium underline-offset-4 hover:text-blue-600 transition-colors duration-300">Our Features</a>
			</div>
  
			<div
			  class="mt-12 flex flex-col items-center justify-center gap-2 sm:flex-row lg:justify-start"
			>
		
			</div>
		  </div>
		  <img
			class="-z-10 order-first ml-auto h-48 w-[72%] object-cover  sm:h-[77px] lg:absolute lg:inset-0 lg:-right-20 lg:-top-72 lg:order-last lg:h-[600px] lg:w-[60%] lg:object-contain dark:mix-blend-lighten dark:invert-0 mt-40 hidden lg:block"
			src="hero.png"
			alt="Abstract Object"
			height="400"
			width="300"
		  />
		</div>
	  </div>
	</section>

  </main>
  
  {#snippet header()}
	<header>
	  <nav class="bg-background/50 fixed z-20 w-full border-b backdrop-blur-3xl">
		<div class="mx-auto max-w-6xl px-6 transition-all duration-300">
		  <div
			class="flex flex-wrap lg:flex-nowrap items-center justify-between gap-6 py-3 lg:gap-6 lg:py-4"
		  >
			<div class="flex w-full items-center justify-between lg:w-auto">
			  <a href="/" aria-label="home" class="flex items-center space-x-2">
				<img src='logonext2.png' alt='logo' width="150" height="50" class="my-custom-class" />
			  </a>
  
			  <button
				onclick={() => (menuState = !menuState)}
				aria-label={menuState == true ? "Close Menu" : "Open Menu"}
				class="relative z-20 -m-2.5 -mr-4 block cursor-pointer p-2.5 lg:hidden"
			  >
				<Menu
				  class={cn(
					"m-auto size-6 duration-200",
					menuState && "rotate-180 scale-0 opacity-0"
				  )}
				/>
				<X
				  class={cn(
					"absolute inset-0 m-auto size-6 -rotate-180 scale-0 opacity-0 duration-200",
					menuState && "rotate-0 scale-100 opacity-100"
				  )}
				/>
			  </button>
			</div>
  
			<div
			  class={[
				"bg-background mb-6 w-full flex-wrap items-center justify-end sm:justify-between space-y-8 rounded-3xl border p-6 shadow-2xl shadow-zinc-300/20 md:flex-nowrap lg:m-0 lg:flex  lg:gap-6 lg:space-y-0 lg:border-transparent lg:bg-transparent lg:p-0 lg:shadow-none dark:shadow-none dark:lg:bg-transparent",
				menuState ? "block lg:flex" : "hidden",
			  ]}
			>
			  <div class="lg:pr-4">
				<ul
				  class="space-y-6 text-base lg:flex lg:gap-8 lg:space-y-0 lg:text-sm"
				>
				  {#each menuItems as item, index}
					<li>
					  <a
						href={item.href}
						class="text-muted-foreground hover:text-accent-foreground block duration-150"
					  >
						<span>{item.name}</span>
					  </a>
					</li>
				  {/each}
				</ul>
			  </div>
  
			  <div
				class="flex w-full flex-col space-y-3 sm:flex-row sm:gap-3 sm:space-y-0 md:w-fit"
			  >
				<Button variant="outline" size="sm">Login</Button>
				<Button size="sm">Sign Up</Button>
			  </div>
			</div>
		  </div>
		</div>
	  </nav>
	</header>
  {/snippet}
  
  {#snippet progressiveBlur({
	direction = "bottom",
	blurLayers = 8,
	class: _class = "",
	blurIntensity = 0.25,
  }: ProgressiveBlurProps)}
	{@const layers = Math.max(blurLayers, 2)}
	{@const segmentSize = 1 / (blurLayers + 1)}
	<div class={cn("relative", _class)}>
	  {#each { length: layers } as _, index}
		{@const angle = GRADIENT_ANGLES[direction]}
		{@const gradientStops = [
		  index * segmentSize,
		  (index + 1) * segmentSize,
		  (index + 2) * segmentSize,
		  (index + 3) * segmentSize,
		].map(
		  (pos, posIndex) =>
			`rgba(255, 255, 255, ${posIndex === 1 || posIndex === 2 ? 1 : 0}) ${pos * 100}%`
		)}
		{@const gradient = `linear-gradient(${angle}deg, ${gradientStops.join(
		  ", "
		)})`}
  
		<div
		  class="pointer-events-none absolute inset-0 rounded-[inherit]"
		  style="mask-image: {gradient};
	-webkit-mask-image: {gradient};
	backdrop-filter: blur({index * blurIntensity}px); z-index: {index * 10};"
		></div>
	  {/each}
	</div>
  {/snippet}



<!-- <section class="bg-gray-50 py-8 -mt-45 border-t border-b border-gray-200"> -->
  <!-- <div class="max-w-6xl mx-auto px-6 text-center">
    <p class="text-gray-500 text-sm mb-6">6K+ providers trust CarePulse</p>
    
    <Marquee pauseOnHover={true} class="py-4">
      <div class="flex items-center px-8">
        <img
          class="mx-auto h-12 w-auto filter grayscale opacity-70"
          src="https://html.tailus.io/blocks/customers/nvidia.svg"
          alt="Partner Logo"
          height="48"
          width="auto"
        />
      </div>

      <div class="flex items-center px-8">
        <img
          class="mx-auto h-12 w-auto filter grayscale opacity-70"
          src="https://html.tailus.io/blocks/customers/column.svg"
          alt="Partner Logo"
          height="48"
          width="auto"
        />
      </div>
      
      <div class="flex items-center px-8">
        <img
          class="mx-auto h-12 w-auto filter grayscale opacity-70"
          src="https://html.tailus.io/blocks/customers/github.svg"
          alt="Partner Logo"
          height="48"
          width="auto"
        />
      </div>
      
      <div class="flex items-center px-8">
        <img
          class="mx-auto h-12 w-auto filter grayscale opacity-70"
          src="https://html.tailus.io/blocks/customers/nike.svg"
          alt="Partner Logo"
          height="48"
          width="auto"
        />
      </div>
      
      <div class="flex items-center px-8">
        <img
          class="mx-auto h-12 w-auto filter grayscale opacity-70"
          src="https://html.tailus.io/blocks/customers/lemonsqueezy.svg"
          alt="Partner Logo"
          height="48"
          width="auto"
        />
      </div>
    </Marquee>
  </div>
</section> -->


