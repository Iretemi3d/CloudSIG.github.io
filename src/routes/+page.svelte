<script lang="ts">
    import Title from "$lib/title.svelte";
    import WhatIsCloud from "$lib/what-is-cloud.svelte";
    import Event from "$lib/event.svelte";
    import Bg from "$lib/bg.svelte";
  
</script>

<Bg/>


<!-- Main content with improved spacing and container -->
<div class="min-h-screen relative">
    <!-- Hero section with title -->
    <section class="relative px-6 md:px-12 lg:px-20 pt-20 pb-16">
        <div class="max-w-7xl mx-auto">
            <Title />
        </div>
    </section>

    <!-- What is Cloud section -->
    <WhatIsCloud />

    <!-- Event section -->
    <section class="relative px-6 md:px-12 lg:px-20 py-16 pb-32">
        <div
            class="max-w-7xl mx-auto backdrop-blur-sm bg-opacity-20 bg-white/5 rounded-2xl p-8 md:p-12 border border-white/10 shadow-2xl"
        >
            <Event />
        </div>
    </section>

    <!-- Decorative bottom gradient -->
    <div
        class="fixed bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-[var(--color-base-1)] to-transparent pointer-events-none"
    ></div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&family=Stack+Sans+Text:wght@200..700&display=swap");

    :global(body) {
        overflow-x: hidden;
    }

    .filter {
        background: radial-gradient(
            circle at center,
            transparent 0%,
            var(--color-base-1) 85%,
            var(--color-base-1) 100%
        );
    }

    /* Smooth scroll behavior */
    :global(html) {
        scroll-behavior: smooth;
    }

    /* Add subtle animation to sections */
    section {
        animation: fadeInUp 0.8s ease-out;
    }

    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(30px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* Stagger animation for sections */
    section:nth-child(2) {
        animation-delay: 0.2s;
        animation-fill-mode: both;
    }

    section:nth-child(3) {
        animation-delay: 0.4s;
        animation-fill-mode: both;
    }

    :global(.font-titles) {
        font-family: "Momo Trust Display", sans-serif;
    }

    /* Enhanced glow effect for interactive elements */
    :global(.glow) {
        box-shadow:
            0 0 20px rgba(21, 228, 255, 0.3),
            0 0 40px rgba(21, 228, 255, 0.2);
    }
</style>
