<script lang="ts">
    let { class: _class = '', width = '180', height = '60' } = $props();
</script>

<svg 
    xmlns="http://www.w3.org/2000/svg" 
    viewBox="0 0 360 120" 
    width={width} 
    height={height} 
    class={_class}
>
    <!-- Circle with C icon -->
    <circle cx="60" cy="60" r="45" fill="#4285F4" />
    <path d="M75 40 C 60 30, 40 40, 35 60 C 30 80, 50 90, 70 80" stroke="white" stroke-width="10" fill="none" stroke-linecap="round" />
    
    <!-- Text: Care -->
    <text x="120" y="70" font-family="Arial, sans-serif" font-size="50" font-weight="bold" fill="#000000">Care</text>
    
    <!-- Text: Pulse -->
    <text x="220" y="70" font-family="Arial, sans-serif" font-size="50" font-weight="bold" fill="#4285F4">Pulse</text>
</svg>