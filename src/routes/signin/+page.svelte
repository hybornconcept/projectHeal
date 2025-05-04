<script lang="ts">
    import type { PageData } from './$types';
    import { Input } from "$lib/components/ui/input/index.js";
    import { Button } from "$lib/components/ui/button/index.js";
    import { User, Mail, Phone } from 'lucide-svelte';

    let { data }: { data: PageData } = $props();

    // Form state
    let fullName = $state('');
    let email = $state('');
    let phoneNumber = $state('');
</script>

<div class="flex min-h-screen">
    <!-- Left side - Form -->
    <div class="w-full lg:w-1/2 bg-black text-white p-8 flex flex-col">
        <!-- Top section with logo and avatars -->
        <div class="mb-16">
            <div class="flex items-center gap-2">
                <div class="bg-teal-500 rounded p-1">
                    <img src="/carepulse-icon.svg" alt="CarePulse" class="w-5 h-5" />
                </div>
                <span class="font-medium">CarePulse</span>
                <div class="ml-2 flex items-center">
                    <div class="bg-white/20 rounded-full w-6 h-6 flex items-center justify-center text-xs">6</div>
                </div>
            </div>
            
            <div class="mt-8 relative">
                <div class="absolute -left-4 -top-4">
                    <div class="relative">
                        <div class="bg-white/10 rounded-full w-8 h-8 absolute -top-2 -left-2"></div>
                        <div class="bg-white/10 rounded-full w-8 h-8 absolute top-0 left-4"></div>
                        <div class="bg-green-500 rounded-full w-10 h-10 flex items-center justify-center text-white font-medium relative z-10">
                            A
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Form content -->
        <div class="mt-8">
            <h1 class="text-3xl font-bold mb-2">Hi there, ...</h1>
            <p class="text-gray-400 mb-8">Get Started with Appointments.</p>
            
            <div class="space-y-6">
                <!-- Full name -->
                <div>
                    <label for="fullName" class="block text-sm text-gray-400 mb-1">Full name</label>
                    <div class="relative">
                        <div class="absolute inset-y-0 left-3 flex items-center">
                            <User size={16} class="text-gray-500" />
                        </div>
                        <Input 
                            id="fullName" 
                            type="text" 
                            placeholder="Adrian Hajdin" 
                            class="pl-10 bg-gray-900 border-gray-800 text-white" 
                            bind:value={fullName} 
                        />
                    </div>
                </div>
                
                <!-- Email address -->
                <div>
                    <label for="email" class="block text-sm text-gray-400 mb-1">Email address</label>
                    <div class="relative">
                        <div class="absolute inset-y-0 left-3 flex items-center">
                            <Mail size={16} class="text-gray-500" />
                        </div>
                        <Input 
                            id="email" 
                            type="email" 
                            placeholder="adrian@jsmastery.pro" 
                            class="pl-10 bg-gray-900 border-gray-800 text-white" 
                            bind:value={email} 
                        />
                    </div>
                </div>
                
                <!-- Phone number -->
                <div>
                    <label for="phone" class="block text-sm text-gray-400 mb-1">Phone number</label>
                    <div class="relative">
                        <div class="absolute inset-y-0 left-3 flex items-center">
                            <Phone size={16} class="text-gray-500" />
                        </div>
                        <Input 
                            id="phone" 
                            type="tel" 
                            placeholder="+00 0342 0453 34" 
                            class="pl-10 bg-gray-900 border-gray-800 text-white" 
                            bind:value={phoneNumber} 
                        />
                    </div>
                </div>
                
                <!-- Submit button -->
                <div class="mt-8">
                    <Button class="w-full bg-emerald-500 hover:bg-emerald-600 text-white py-6">
                        Get Started
                    </Button>
                </div>
            </div>
        </div>
        
        <!-- Footer -->
        <div class="mt-auto pt-8 text-xs text-gray-500">
            @carepulse copyright
        </div>
    </div>
    
    <!-- Right side - Image -->
    <div class="hidden lg:block lg:w-1/2">
        <img 
            src="https://img.freepik.com/free-photo/doctor-with-his-arms-crossed-white-background_1368-5790.jpg" 
            alt="Doctor portrait" 
            class="w-full h-full object-cover"
        />
    </div>
</div>