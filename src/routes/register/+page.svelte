<script lang="ts">
    import { Button } from "$lib/components/ui/button/index.js";
    import { Input } from "$lib/components/ui/input/index.js";
    import { Label } from "$lib/components/ui/label/index.js";
    import * as Card from "$lib/components/ui/card/index.js";
    import { Checkbox } from "$lib/components/ui/checkbox/index.js";
    import { 
        Eye, 
        EyeOff, 
        Activity, 
        Mail, 
        Lock, 
        Facebook, 
    } from "lucide-svelte";
    
    let showPassword = $state(false);
    const togglePasswordVisibility = () => {
        showPassword = !showPassword;
    };
</script>

<div class="w-full min-h-screen flex items-center justify-center p-[4%]">
  <Card.Root class="w-full max-w-6xl">
    <Card.Content class="p-2">
      <div class="w-full lg:grid lg:min-h-[600px] lg:grid-cols-2 xl:min-h-[800px]">
        <div class="flex items-center justify-center py-10">
          <div class="mx-auto w-[350px] space-y-5">
            <!-- Logo -->
            <div class="mb-5">
              <div class="bg-blue-600 text-white w-8 h-8 rounded flex items-center justify-center">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 12h-4l-3 9L9 3l-3 9H2"/></svg>
              </div>
            </div>
            
            <!-- Header -->
            <div class="space-y-2">
              <h1 class="text-2xl font-bold">Log in to your Account</h1>
              <p class="text-gray-600 text-sm">Welcome back! Select method to log in:</p>
            </div>
            
            <!-- Social login buttons -->
            <div class="grid grid-cols-2 gap-4">
              <Button variant="outline" class="flex items-center justify-center gap-2 h-11">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24">
                  <path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/>
                  <path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/><path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z"/><path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"/></svg>
                Google
              </Button>
              <Button variant="outline" class="flex items-center justify-center gap-2 h-11">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="#1877F2"><path d="M24 12.073c0-5.8-4.698-10.5-10.498-10.5s-10.5 4.7-10.5 10.5c0 5.242 3.837 9.584 8.997 10.37v-7.336H8.747v-3.037h3.252V9.739c0-3.21 1.912-4.983 4.842-4.983 1.397 0 2.845.25 2.845.25v3.126h-1.6c-1.58 0-2.072.98-2.072 1.982v2.383h3.528l-.565 3.037h-2.963V22.5A10.5 10.5 0 0024 12.073z"/></svg>
                Facebook
              </Button>
            </div>
            
            <div class="relative flex items-center justify-center">
              <div class="border-t border-gray-200 w-full"></div>
              <span class="bg-white px-2 text-xs text-gray-500 absolute">or continue with email</span>
            </div>
            
            <!-- Form -->
            <form class="space-y-4">
              <div class="space-y-1">
                <Label for="email" class="sr-only">Email</Label>
                <div class="flex items-center border rounded-md px-3 focus-within:ring-2 focus-within:ring-blue-600 focus-within:border-blue-600">
                  <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-gray-400"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
                  <Input id="email" type="email" placeholder="Email" class="border-0 focus-visible:ring-0 focus-visible:ring-offset-0" required />
                </div>
              </div>
              
              <div class="space-y-1">
                <Label for="password" class="sr-only">Password</Label>
                <div class="flex items-center border rounded-md px-3 focus-within:ring-2 focus-within:ring-blue-600 focus-within:border-blue-600">
                  <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-gray-400"><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
                  <Input 
                    id="password" 
                    type={showPassword ? "text" : "password"} 
                    placeholder="Password" 
                    class="border-0 focus-visible:ring-0 focus-visible:ring-offset-0" 
                    required 
                  />
                  <button 
                      onclick={() => togglePasswordVisibility()} 
                      type="button" 
                      class="absolute right-3 top-1/2 -translate-y-1/2"
                  >
                      {#if showPassword}
                          <EyeOff class="h-5 w-5 text-gray-500" />
                      {:else}
                          <Eye class="h-5 w-5 text-gray-500" />
                      {/if}
                  </button>
                </div>
              </div>
              
              <div class="flex items-center justify-between">
                <div class="flex items-center space-x-2">
                  <Checkbox id="remember" />
                  <label for="remember" class="text-sm text-gray-600">Remember me</label>
                </div>
                <a href="##" class="text-sm text-blue-600 hover:underline">
                  Forgot Password?
                </a>
              </div>
              
              <Button type="submit" class="w-full bg-blue-600 hover:bg-blue-700 h-11">Log in</Button>
              
              <div class="text-center text-sm text-gray-600">
                Don't have an account? 
                <a href="##" class="text-blue-600 hover:underline">Create an account</a>
              </div>
            </form>
          </div>
        </div>
        <div class="bg-muted hidden lg:block">
          <img
            src="https://img.freepik.com/free-photo/stethoscope-copy-space_23-2147652347.jpg"
            alt="Stethoscope on medical background"
            width="1920"
            height="1080"
            class="h-full w-full object-cover"
          />
        </div>
      </div>
    </Card.Content>
  </Card.Root>
</div>
