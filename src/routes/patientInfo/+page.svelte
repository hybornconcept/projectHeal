<script lang="ts">
    import type { PageData } from './$types';
    import { Button } from "$lib/components/ui/button/index.js";
    import { Input } from "$lib/components/ui/input/index.js";
    import { Calendar } from 'lucide-svelte';
    import { Phone } from 'lucide-svelte';
    import * as Select from "$lib/components/ui/select/index.js";
    import * as RadioGroup from "$lib/components/ui/radio-group/index.js";
    import { Textarea } from "$lib/components/ui/textarea/index.js";
    import { Checkbox } from "$lib/components/ui/checkbox/index.js";
    import * as Card from "$lib/components/ui/card/index.js";
    import { Label } from "$lib/components/ui/label/index.js";
    import * as Tooltip from "$lib/components/ui/tooltip/index.js";

    let { data }: { data: PageData } = $props();
    
    // Form state
    let fullName = $state('');
    let email = $state('');
    let phoneNumber = $state('');
    let birthDate = $state('');
    let gender = $state('Male');
    let address = $state('');
    let occupation = $state('');
    let emergencyContactName = $state('');
    let emergencyPhoneNumber = $state('');
    
    // Medical information state
    let insuranceProvider = $state('');
    let policyNumber = $state('');
    let allergies = $state('');
    let medications = $state('');
    let familyHistory = $state('');
    let medicalHistory = $state('');
    let identificationNumber = $state('');
    
    // Consent state
    let consentTreatment = $state(false);
    let consentDisclosure = $state(false);
    let consentPrivacy = $state(false);
    
    // Select options
    const physicians = [
        { value: "dr-smith", label: "Dr. Adam Smith", color: "blue" },
        { value: "dr-johnson", label: "Dr. Barbara Johnson", color: "green" }
    ];
    
    const idTypes = [
        { value: "birth-certificate", label: "Birth Certificate" },
        { value: "passport", label: "Passport" },
        { value: "drivers-license", label: "Driver's License" },
        { value: "national-id", label: "National ID" }
    ];
    
    // Select state
    let selectedPhysician = $state("");
    let selectedIdType = $state("");
    
    // Derived values for select triggers
    const physicianTriggerContent = $derived(
        physicians.find((p) => p.value === selectedPhysician)?.label ?? "Select a physician"
    );
    
    const idTypeTriggerContent = $derived(
        idTypes.find((t) => t.value === selectedIdType)?.label ?? "Select identification type"
    );
</script>

<div class="min-h-screen bg-gray-50 py-8 px-4">
  <Tooltip.Provider>
    <div class="max-w-6xl mx-auto bg-white rounded-xl shadow-lg overflow-hidden">
      <div class="flex flex-col lg:flex-row">
        <!-- Left side - Form (70%) -->
        <div class="w-full lg:w-[70%] pl-[5%] pr-8 py-8 lg:py-10 overflow-y-auto">
          <div class="max-w-3xl mx-auto">
            <!-- Logo and header -->
            <div class="mb-8">
              <div class="mb-6">
                <img 
                  src="/logonext2.png" 
                  alt="CarePulse Logo" 
                  width="150" 
                  height="50" 
                  class="my-custom-class" 
                />
              </div>
              
              <h1 class="text-3xl font-bold mb-1">Welcome 👋</h1>
              <p class="text-gray-600">Let us know more about yourself</p>
            </div>
            
            <!-- Form content -->
            <div class="space-y-8">
              <!-- Personal Information Form -->
              <div>
                  <h2 class="text-xl font-semibold mb-6">Personal Information</h2>
                  
                  <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                      <!-- Full name -->
                      <div>
                          <label for="fullName" class="block text-sm font-medium text-gray-700 mb-1">Full name</label>
                          <Input id="fullName" type="text" placeholder="ex: Oluwaseun Adeyemi" bind:value={fullName} />
                      </div>
                      
                      <!-- Email address -->
                      <div>
                          <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email address</label>
                          <Input id="email" type="email" placeholder="oluwaseun@gmail.com" bind:value={email} />
                      </div>
                      
                      <!-- Phone number -->
                      <div>
                          <label for="phone" class="block text-sm font-medium text-gray-700 mb-1">Phone number</label>
                          <div class="relative">
                              <div class="absolute inset-y-0 left-3 flex items-center">
                                  <Phone size={16} class="text-gray-400" />
                              </div>
                              <Input id="phone" type="tel" placeholder="+234 803 123 4567" class="pl-10" bind:value={phoneNumber} />
                          </div>
                      </div>
                      
                      <!-- Date of birth -->
                      <div>
                          <label for="birthDate" class="block text-sm font-medium text-gray-700 mb-1">Date of birth</label>
                          <div class="relative">
                              <div class="absolute inset-y-0 left-3 flex items-center">
                                  <Calendar size={16} class="text-gray-400" />
                              </div>
                              <Input id="birthDate" type="text" placeholder="Select your birth date" class="pl-10" bind:value={birthDate} />
                          </div>
                      </div>
                      
                      <!-- Gender -->
                      <div>
                          <label class="block text-sm font-medium text-gray-700 mb-1">Gender</label>
                          <RadioGroup.Root bind:value={gender} class="flex gap-4">
                              <div class="flex items-center space-x-2">
                                  <RadioGroup.Item value="Male" id="male" />
                                  <label for="male" class="text-sm text-gray-700">Male</label>
                              </div>
                              <div class="flex items-center space-x-2">
                                  <RadioGroup.Item value="Female" id="female" />
                                  <label for="female" class="text-sm text-gray-700">Female</label>
                              </div>
                              <div class="flex items-center space-x-2">
                                  <RadioGroup.Item value="Other" id="other" />
                                  <label for="other" class="text-sm text-gray-700">Other</label>
                              </div>
                          </RadioGroup.Root>
                      </div>
                      
                      <!-- Address -->
                      <div>
                          <label for="address" class="block text-sm font-medium text-gray-700 mb-1">Address</label>
                          <Input id="address" type="text" placeholder="ex: 15 Awolowo Road, Ikoyi, Lagos" bind:value={address} />
                      </div>
                      
                      <!-- Occupation -->
                      <div>
                          <label for="occupation" class="block text-sm font-medium text-gray-700 mb-1">Occupation</label>
                          <Input id="occupation" type="text" placeholder="ex: Civil Servant" bind:value={occupation} />
                      </div>
                      
                      <!-- Emergency contact name -->
                      <div>
                          <label for="emergencyName" class="block text-sm font-medium text-gray-700 mb-1">Emergency contact name</label>
                          <Input id="emergencyName" type="text" placeholder="ex: Chinedu Okonkwo" bind:value={emergencyContactName} />
                      </div>
                      
                      <!-- Emergency Phone number -->
                      <div>
                          <label for="emergencyPhone" class="block text-sm font-medium text-gray-700 mb-1">Emergency Phone number</label>
                          <div class="relative">
                              <div class="absolute inset-y-0 left-3 flex items-center">
                                  <Phone size={16} class="text-gray-400" />
                              </div>
                              <Input id="emergencyPhone" type="tel" placeholder="ex: +234 805 678 9012" class="pl-10" bind:value={emergencyPhoneNumber} />
                          </div>
                      </div>
                  </div>
              </div>
              
              <!-- Medical Information -->
              <div>
                  <h2 class="text-xl font-semibold mb-6">Medical Information</h2>
                  
                  <div class="space-y-6">
                      <!-- Primary care physician -->
                      <div>
                          <Label for="physician-select" class="block text-sm font-medium text-gray-700 mb-1">Primary care physician</Label>
                          <Select.Root type="single" bind:value={selectedPhysician}>
                              <Select.Trigger class="w-full" id="physician-select">
                                  {physicianTriggerContent}
                              </Select.Trigger>
                              <Select.Content>
                                  <Select.Group>
                                      <Select.GroupHeading>Available Physicians</Select.GroupHeading>
                                      {#each physicians as physician (physician.value)}
                                          <Select.Item value={physician.value} label={physician.label}>
                                              <div class="flex items-center">
                                                  <div class="bg-{physician.value === 'dr-smith' ? 'blue' : 'green'}-500 text-white rounded-full w-5 h-5 flex items-center justify-center mr-2">
                                                      {physician.label[3]}
                                                  </div>
                                                  <span>{physician.label}</span>
                                              </div>
                                          </Select.Item>
                                      {/each}
                                  </Select.Group>
                              </Select.Content>
                          </Select.Root>
                      </div>
                      
                      <!-- Insurance information -->
                      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                          <div>
                              <Label for="insuranceProvider" class="block text-sm font-medium text-gray-700 mb-1">Insurance provider</Label>
                              <Input id="insuranceProvider" placeholder="ex: NHIS or Hygeia HMO" bind:value={insuranceProvider} />
                          </div>
                          <div>
                              <Label for="policyNumber" class="block text-sm font-medium text-gray-700 mb-1">Insurance policy number</Label>
                              <Input id="policyNumber" placeholder="ex: NHIS-123456789" bind:value={policyNumber} />
                          </div>
                      </div>
                      
                      <!-- Medical details -->
                      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                          <div>
                              <Label for="allergies" class="block text-sm font-medium text-gray-700 mb-1">Allergies (if any)</Label>
                              <Textarea id="allergies" placeholder="ex: Groundnuts, Sulfa drugs, Dust" bind:value={allergies} />
                          </div>
                          <div>
                              <Label for="medications" class="block text-sm font-medium text-gray-700 mb-1">Current medications</Label>
                              <Textarea id="medications" placeholder="e.g. Lisinopril 10mg, Paracetamol 500mg" bind:value={medications} />
                          </div>
                      </div>
                      
                      <!-- Medical history -->
                      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                          <div>
                              <Label for="familyHistory" class="block text-sm font-medium text-gray-700 mb-1">Family medical history (if relevant)</Label>
                              <Textarea id="familyHistory" placeholder="ex: Mother had breast cancer" bind:value={familyHistory} />
                          </div>
                          <div>
                              <Label for="medicalHistory" class="block text-sm font-medium text-gray-700 mb-1">Past medical history</Label>
                              <Textarea id="medicalHistory" placeholder="ex: Asthma diagnosis in childhood" bind:value={medicalHistory} />
                          </div>
                      </div>
                  </div>
              </div>
              
              <!-- Identification and Verification -->
              <div>
                  <h2 class="text-xl font-semibold mb-6">Identification and Verification</h2>
                  
                  <div class="space-y-6">
                      <!-- Identification type -->
                      <div>
                          <Label for="id-type-select" class="block text-sm font-medium text-gray-700 mb-1">Identification type</Label>
                          <Select.Root type="single" bind:value={selectedIdType}>
                              <Select.Trigger class="w-full" id="id-type-select">
                                  {idTypeTriggerContent}
                              </Select.Trigger>
                              <Select.Content>
                                  <Select.Group>
                                      <Select.GroupHeading>ID Types</Select.GroupHeading>
                                      {#each idTypes as idType (idType.value)}
                                          <Select.Item value={idType.value} label={idType.label} />
                                      {/each}
                                  </Select.Group>
                              </Select.Content>
                          </Select.Root>
                      </div>
                      
                      <!-- Identification Number -->
                      <div>
                          <Label for="identificationNumber" class="block text-sm font-medium text-gray-700 mb-1">Identification Number</Label>
                          <Input id="identificationNumber" placeholder="ex: 1234567" bind:value={identificationNumber} />
                      </div>
                      
                      <!-- Scanned Copy of Identification Document -->
                      <div>
                          <Label for="idDocument" class="block text-sm font-medium text-gray-700 mb-1">Scanned Copy of Identification Document</Label>
                          <div id="idDocument" class="border border-gray-300 rounded p-8 text-center bg-gray-50">
                              <p class="text-blue-500 mb-1">Click to upload</p>
                              <p class="text-gray-500 text-sm">or drag and drop</p>
                              <p class="text-gray-400 text-xs mt-1">(PDF, JPG, PNG max: 10MB/file)</p>
                          </div>
                      </div>
                  </div>
              </div>
              
              <!-- Consent and Privacy -->
              <div>
                  <h2 class="text-xl font-semibold mb-6">Consent and Privacy</h2>
                  
                  <div class="space-y-4">
                      {#each [
                          { id: 'consent-treatment', checked: consentTreatment, label: 'I consent to receive treatment for my health condition.' },
                          { id: 'consent-disclosure', checked: consentDisclosure, label: 'I consent to the use and disclosure of my health information for treatment purposes.' },
                          { id: 'consent-privacy', checked: consentPrivacy, label: 'I acknowledge that I have reviewed and agree to the privacy policy' }
                      ] as consent}
                          <div class="flex items-start space-x-2">
                              <Checkbox id={consent.id} bind:checked={consent.checked} />
                              <label for={consent.id} class="text-sm text-gray-700">
                                  {consent.label}
                              </label>
                          </div>
                      {/each}
                  </div>
              </div>
              
              <!-- Submit button -->
              <div class="w-full mt-6">
                  <Button class="w-full bg-blue-500 hover:bg-green-600 text-white px-6">Submit and continue</Button>
              </div>
          </div>
        </div>
        
      
      </div>
        <!-- Right side - Medical Image (30%) -->
        <div class="hidden lg:block lg:w-[30%] bg-blue-50 relative">
            <img 
              src="https://img.freepik.com/free-photo/doctor-with-his-arms-crossed-white-background_1368-5790.jpg" 
              alt="Nigerian doctor"
              class="w-full h-full object-cover"
            />
          </div>
    </div>
  </Tooltip.Provider>
</div>

