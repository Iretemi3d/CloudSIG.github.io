<script lang="ts">
    import Title from "$lib/title.svelte";
    import WhatIsCloud from "$lib/what-is-cloud.svelte";
    import Event from "$lib/event.svelte";
    import Bg from "$lib/bg.svelte";
    import Foot from "$lib/foot.svelte";
</script>

<Bg />

<div class="min-h-screen relative text-slate-200">
    <div
        class="fixed inset-0 z-[-1] opacity-10 pointer-events-none"
        style="background-image: linear-gradient(#1e293b 1px, transparent 1px), linear-gradient(90deg, #1e293b 1px, transparent 1px); background-size: 60px 60px;"
    ></div>

    <main class="relative z-10">
        <section
            class="relative px-6 md:px-12 lg:px-20 pt-20 pb-16 overflow-hidden"
        >
            <div
                class="absolute top-20 right-[10%] w-64 h-64 bg-cyan-500/10 blur-[100px] rounded-full animate-pulse"
            ></div>

            <div class="max-w-7xl mx-auto">
                <Title />
            </div>
        </section>

        <WhatIsCloud />

        <section class="relative px-6 md:px-12 lg:px-20 py-16 pb-32">
            <div class="max-w-7xl mx-auto">
                <div
                    class="group relative rounded-[40px] p-[1px] overflow-hidden bg-white/10 transition-all duration-500"
                >
                    <div
                        class="absolute inset-[-1000%] animate-[spin_8s_linear_infinite] bg-[conic-gradient(from_90deg_at_50%_50%,#00c2ff_0%,#15e4ff_50%,#00c2ff_100%)] opacity-20 group-hover:opacity-100 transition-opacity"
                    ></div>

                    <div
                        class="relative backdrop-blur-3xl bg-slate-950/80 rounded-[39px] p-8 md:p-12 border border-white/5 shadow-2xl"
                    >
                        <div class="flex items-center gap-4 mb-8">
                            <div
                                class="h-[1px] flex-grow bg-gradient-to-r from-transparent to-cyan-500/50"
                            ></div>
                            <span
                                class="font-mono text-cyan-400 text-xs tracking-widest uppercase"
                                >Upcoming Transmission</span
                            >
                            <div
                                class="h-[1px] flex-grow bg-gradient-to-l from-transparent to-cyan-500/50"
                            ></div>
                        </div>

                        <Event />
                    </div>
                </div>
            </div>
        </section>
    </main>

    <Foot />

    <div
        class="fixed bottom-0 left-0 right-0 h-40 bg-gradient-to-t from-[#030712] via-[#030712]/80 to-transparent pointer-events-none z-20"
    ></div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&family=Stack+Sans+Text:wght@200..700&display=swap");

    :global(body) {
        background-color: #030712; /* Deep space black */
        color: #e2e8f0;
        overflow-x: hidden;
    }

    /* Global smooth scrolling */
    :global(html) {
        scroll-behavior: smooth;
    }

    /* Section Entrance Animations */
    section {
        opacity: 0;
        transform: translateY(30px);
        animation: fadeInUp 1s cubic-bezier(0.22, 1, 0.36, 1) forwards;
    }

    @keyframes fadeInUp {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* Staggered entrance */
    section:nth-child(1) {
        animation-delay: 0.1s;
    }
    section:nth-child(2) {
        animation-delay: 0.3s;
    }
    section:nth-child(3) {
        animation-delay: 0.5s;
    }

    /* Techy Text Shadow for Headlines */
    :global(.text-highlight) {
        text-shadow: 0 0 30px rgba(21, 228, 255, 0.3);
    }
</style>
