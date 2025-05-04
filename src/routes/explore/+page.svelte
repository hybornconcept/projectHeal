<script lang="ts">
    import type { PageData } from './$types';
    import { MapPin, Star, Search, CircleDot } from 'lucide-svelte';
    import { Slider } from "$lib/components/ui/slider/index.js";
    import { Checkbox } from "$lib/components/ui/checkbox/index.js";
    import { Button } from "$lib/components/ui/button/index.js";
    import * as Card from "$lib/components/ui/card/index.js";
    import { Input } from "$lib/components/ui/input/index.js";
    import * as Select from "$lib/components/ui/select/index.js";
    import { Badge } from "$lib/components/ui/badge/index.js";

    let { data }: { data: PageData } = $props();
    
    // Specialties data
    const specialties = [
        { value: "", label: "All specialties" },
        { value: "General Physician", label: "General Physician" },
        { value: "Pediatrics", label: "Pediatrics" },
        { value: "Cardiology", label: "Cardiology" },
        { value: "Neurology", label: "Neurology" }
    ];
    const facilities = [
        { value: "", label: "All facilities" },
        { value: "Facility 1", label: "Facility 1" },
        { value: "Facility 2", label: "Facility 2" },
        { value: "facility 3", label: "facility 3" },
        { value: "Facility 4", label: "Facility 4" }
    ];
    
    // States
    let selectedSpecialty = $state('');
    let selectedfacility= $state('');
    
    // Derive the trigger content
    const facilityTriggerContent = $derived(
        facilities.find((s) => s.value === selectedfacility)?.label ?? "Select facility"
    );

        // Derive the trigger content
        const specialtyTriggerContent = $derived(
        specialties.find((s) => s.value === selectedSpecialty)?.label ?? "Select specialty"
    );
    
    
    // Rest of your state variables
    let minFee = $state(0);
    let maxFee = $state(8000);
    let feeValue = $state([minFee, maxFee]);
    let searchQuery = $state('');
    let onlineNow = $state(false);
    let availableIn2Hours = $state(false);
    let availableToday = $state(false);
    let anyGender = $state(false);
    let male = $state(false);
    let female = $state(false);
    let doctorsCount = $state(994);
    


    // Update min and max fee when slider value changes
    $effect(() => {
        minFee = feeValue[0];
        maxFee = feeValue[1];
    });


    
    // Doctor data
    const doctors = [
        {
            id: 1,
            name: 'Dr. Oluwaseun Adeyemi',
            image: 'https://img.freepik.com/free-photo/close-up-health-worker_23-2149112513.jpg?ga=GA1.1.1701402532.1745516278&semt=ais_hybrid&w=740',
            degree: 'MBBS, FWACP',
            hospital: 'Lagos University Teaching Hospital',
            specialties: ['General Physician', 'Pediatrics'],
            rating: 4.6,
            reviews: 136,
            experience: '10+ Years',
            fee: 15000,
            verified: true
        },
        {
            id: 2,
            name: 'Dr. Chukwudi Okonkwo',
            image: 'https://img.freepik.com/free-photo/black-nurse-man-getting-ready-work_52683-92787.jpg?ga=GA1.1.1701402532.1745516278&semt=ais_hybrid&w=740',
            degree: 'MBBS, FMCP',
            hospital: 'National Hospital Abuja',
            specialties: ['General Physician', 'Cardiology'],
            rating: 4.5,
            reviews: 126,
            experience: '13+ Years',
            fee: 18000,
            verified: true
        },
        {
            id: 3,
            name: 'Dr. Amina Ibrahim',
            image: 'https://img.freepik.com/free-photo/doctor-with-stethoscope-hand-her-pocket-closeup-female-smiling-while-standing-straight-white-background_657921-731.jpg?ga=GA1.1.1701402532.1745516278&semt=ais_hybrid&w=740',
            degree: 'MBBS, FWACP',
            hospital: 'University College Hospital, Ibadan',
            specialties: ['General Physician', 'Neurology'],
            rating: 4.7,
            reviews: 134,
            experience: '7+ Years',
            fee: 20000,
            verified: true
        }
    ];

    function clearAllFilters() {
        minFee = 0;
        maxFee = 8000;
        feeValue = [minFee, maxFee];
        searchQuery = '';
        selectedSpecialty = '';
        onlineNow = false;
        availableIn2Hours = false;
        availableToday = false;
        anyGender = false;
        male = false;
        female = false;
    }

    // Update min and max fee when slider value changes
    $effect(() => {
        minFee = feeValue[0];
        maxFee = feeValue[1];
    });
</script>

<div class="mx-auto max-w-7xl px-4 py-6 bg-gray-50">
    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
        <!-- Left sidebar - Filters -->
        <Card.Root>
            <Card.Header class="pb-2">
                <div class="flex justify-between items-center">
                    <Card.Title>Filters</Card.Title>
                    <Button variant="ghost" size="sm" class="text-green-500 hover:text-green-600 h-auto p-0" onclick={clearAllFilters}>
                        Clear All
                    </Button>
                </div>
            </Card.Header>
            <Card.Content class="space-y-6">
                <!-- Consultation Fee Range -->
                <div>
                    <h3 class="text-sm font-medium text-gray-900 mb-4">Consultation Fee</h3>
                    <div class="mb-6">
                        <Slider type="multiple" bind:value={feeValue} max={8000} step={100} class="max-w-[90%] mx-auto" />
                    </div>
                    <div class="flex justify-between">
                        <Badge variant="outline">₦{minFee}</Badge>
                        <Badge variant="outline">₦{maxFee}</Badge>
                    </div>
                </div>
                
                <!-- Mode of Consult -->
                <div>
                    <h3 class="text-sm font-medium text-gray-900 mb-4">Mode of Consult</h3>
                    <div class="space-y-3">
                        <div class="flex items-center space-x-2">
                            <Checkbox id="online-now" bind:checked={onlineNow} />
                            <label for="online-now" class="text-sm text-gray-700 leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70">
                                Online Now
                            </label>
                        </div>
                        <div class="flex items-center space-x-2">
                            <Checkbox id="available-2-hours" bind:checked={availableIn2Hours} />
                            <label for="available-2-hours" class="text-sm text-gray-700 leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70">
                                Available in next 2 hours
                            </label>
                        </div>
                        <div class="flex items-center space-x-2">
                            <Checkbox id="available-today" bind:checked={availableToday} />
                            <label for="available-today" class="text-sm text-gray-700 leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70">
                                Available today
                            </label>
                        </div>
                    </div>
                </div>
                
                <!-- Gender -->
                <div>
                    <h3 class="text-sm font-medium text-gray-900 mb-4">Gender</h3>
                    <div class="space-y-3">
                        <div class="flex items-center space-x-2">
                            <Checkbox id="any-gender" bind:checked={anyGender} />
                            <label for="any-gender" class="text-sm text-gray-700 leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70">
                                Any Gender
                            </label>
                        </div>
                        <div class="flex items-center space-x-2">
                            <Checkbox id="male" bind:checked={male} />
                            <label for="male" class="text-sm text-gray-700 leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70">
                                Male
                            </label>
                        </div>
                        <div class="flex items-center space-x-2">
                            <Checkbox id="female" bind:checked={female} />
                            <label for="female" class="text-sm text-gray-700 leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70">
                                Female
                            </label>
                        </div>
                    </div>
                </div>
                
                <!-- Sort By Rating -->
                <div>
                    <h3 class="text-sm font-medium text-gray-900 mb-4">Sort By Rating</h3>
                    <div class="flex text-yellow-400">
                        {#each Array(5) as _, i}
                            <Star size={16} fill="currentColor" class="mr-0.5" />
                        {/each}
                    </div>
                </div>
            </Card.Content>
        </Card.Root>

        <!-- Right content -->
        <div class="md:col-span-3">
            <!-- Search and filter bar -->
            <div class="flex flex-col md:flex-row gap-4 mb-6">
                <div class="relative flex-grow">
                    <div class="absolute inset-y-0 left-3 flex items-center pointer-events-none">
                        <Search size={20} class="text-gray-400" />
                    </div>
                    <Input 
                        type="text" 
                        placeholder="Find Your Doctor" 
                        class="pl-10"
                        bind:value={searchQuery}
                    />
                </div>
                
                <Select.Root type="single" bind:value={selectedfacility}>
                    <Select.Trigger class="w-full md:w-64">
                        {facilityTriggerContent}
                    </Select.Trigger>
                    <Select.Content>
                        <Select.Group>
                            {#each facilities as facility (facility.value)}
                                <Select.Item value={facility.value} label={facility.label} />
                            {/each}
                        </Select.Group>
                    </Select.Content>
                </Select.Root>
                
                <Select.Root type="single" bind:value={selectedSpecialty}>
                    <Select.Trigger class="w-full md:w-64">
                        {specialtyTriggerContent}
                    </Select.Trigger>
                    <Select.Content>
                        <Select.Group>
                            {#each specialties as specialty (specialty.value)}
                                <Select.Item value={specialty.value} label={specialty.label} />
                            {/each}
                        </Select.Group>
                    </Select.Content>
                </Select.Root>
            </div>
            
            <!-- Doctors count and view all -->
            <div class="flex justify-between items-center mb-6">
                <p class="text-gray-700 text-sm">
                    <span class="font-semibold">{doctorsCount}</span> Doctors found in <span class="font-semibold">General Physician</span> department
                </p>
                <Button variant="link" class="h-auto p-0 text-blue-500 hover:text-blue-600">View All</Button>
            </div>
            
            <!-- Doctor listings -->
            <div class="space-y-4">
                {#each doctors as doctor}
                    <Card.Root>
                        <Card.Content class="p-4">
                            <div class="flex items-center">
                                <!-- Doctor image -->
                                <div class="w-20 h-20 flex-shrink-0 mr-4">
                                    <img 
                                        src={doctor.image} 
                                        alt={doctor.name} 
                                        class="w-full h-full object-cover rounded-lg"
                                    />
                                </div>
                                
                                <!-- Doctor info -->
                                <div class="flex-grow">
                                    <div class="flex items-center">
                                        <Card.Title class="text-lg font-semibold text-gray-900">{doctor.name}</Card.Title>
                                        {#if doctor.verified}
                                            <span class="text-green-500 ml-1">
                                                <CircleDot size={16} fill="currentColor" />
                                            </span>
                                        {/if}
                                    </div>
                                    <p class="text-gray-600 text-sm">{doctor.degree}</p>
                                    <p class="text-gray-600 text-sm flex items-center mt-1">
                                        <MapPin size={14} class="mr-1 text-gray-500" />
                                        {doctor.hospital}
                                    </p>
                                    
                                    <!-- Specialties -->
                                    <div class="mt-2 flex flex-wrap items-center">
                                        <span class="text-sm text-gray-600 mr-2">Specialties:</span>
                                        {#each doctor.specialties as specialty}
                                            <Badge variant="secondary" class="mr-2">{specialty}</Badge>
                                        {/each}
                                        <span class="text-blue-500 text-sm">2+</span>
                                    </div>
                                    
                                    <!-- Rating -->
                                    <div class="flex items-center mt-2">
                                        <div class="flex text-yellow-400 mr-2">
                                            {#each Array(5) as _}
                                                <Star size={14} fill="currentColor" class="mr-0.5" />
                                            {/each}
                                        </div>
                                        <span class="text-sm text-gray-700">{doctor.rating} ({doctor.reviews} Reviews)</span>
                                    </div>
                                </div>
                                
                                <!-- Price and buttons side by side -->
                                <div class="flex items-center gap-4">
                                    <!-- Price section -->
                                    <div class="text-right">
                                        <div class="flex items-center justify-end">
                                            <span class="text-gray-500 mr-1">₦</span>
                                            <span class="text-2xl font-bold text-gray-900">{doctor.fee}</span>
                                            <span class="text-xs text-gray-500 ml-1">(incl.VAT)</span>
                                        </div>
                                        <p class="text-sm text-gray-500">Per consultation</p>
                                        <p class="text-xs text-gray-400 line-through">Before ₦510</p>
                                    
                                        <div class="mt-1">
                                            <p class="text-sm text-gray-500">Experience</p>
                                            <p class="text-base font-medium text-gray-900">{doctor.experience}</p>
                                        </div>
                                    </div>
                                    
                                    <!-- Buttons section -->
                                    <div class="flex flex-col gap-2 w-32">
                                        <Button variant="outline" class="rounded-full border-blue-500 text-blue-500 hover:bg-blue-50">View Profile</Button>
                                        <Button class="rounded-full bg-blue-500 hover:bg-blue-600">Book Now</Button>
                                    </div>
                                </div>
                            </div>
                        </Card.Content>
                    </Card.Root>
                {/each}
            </div>
        </div>
    </div>
</div>
