<script lang="ts" context="module">
    export interface EventCard {
        id: number;
        title: string;
        date: string;
        summary: string;
    }
</script>

<script lang="ts">
    // Using $state for Svelte 5 reactivity
    let events = $state<EventCard[]>([
        {
            id: 1,
            title: "Intro to Cloud",
            date: "Jan 12, 2026",
            summary: "Kickoff session covering basics of cloud models.",
        },
        {
            id: 2,
            title: "Coming soon",
            date: "TBA",
            summary: "Synchronizing next transmission...",
        },
    ]);

    let scroller = $state<HTMLDivElement | null>(null);

    function scrollByCards(direction: 1 | -1) {
        if (!scroller) return;
        const cardWidth = 320 + 25; // card width + gap
        scroller.scrollBy({ left: direction * cardWidth, behavior: "smooth" });
    }

    function handleWheel(e: WheelEvent) {
        if (!scroller) return;
        // Natural horizontal scrolling
        const delta =
            Math.abs(e.deltaY) > Math.abs(e.deltaX) ? e.deltaY : e.deltaX;
        scroller.scrollBy({ left: delta, behavior: "auto" });
    }
</script>

<div class="relative w-full overflow-visible">
    <div class="flex items-center justify-between mb-8 px-4">
        <h2 class="text-2xl font-mono text-cyan-400 tracking-tighter uppercase">
            <span
                class="inline-block w-2 h-2 bg-cyan-400 rounded-full animate-ping mr-2"
            ></span>
            Event_Log
        </h2>

        <div class="flex gap-2">
            <button
                onclick={() => scrollByCards(-1)}
                class="w-10 h-10 flex items-center justify-center rounded-full border border-white/10 bg-white/5 hover:bg-cyan-500 hover:text-slate-950 transition-all text-white"
                aria-label="Previous"
            >
                ◄
            </button>
            <button
                onclick={() => scrollByCards(1)}
                class="w-10 h-10 flex items-center justify-center rounded-full border border-white/10 bg-white/5 hover:bg-cyan-500 hover:text-slate-950 transition-all text-white"
                aria-label="Next"
            >
                ►
            </button>
        </div>
    </div>

    <div
        bind:this={scroller}
        onwheel={handleWheel}
        class="flex gap-8 overflow-x-auto snap-x snap-mandatory scrollbar-none py-10 px-4 cursor-grab active:cursor-grabbing"
    >
        {#each events as ev}
            <article
                class="group relative flex-none w-[300px] md:w-[350px] snap-start"
                aria-labelledby={`ev-${ev.id}-title`}
            >
                <div
                    class="absolute -inset-2 bg-cyan-500/0 group-hover:bg-cyan-500/10 blur-2xl rounded-[32px] transition-all duration-500"
                ></div>

                <div
                    class="relative h-full p-8 bg-slate-900/50 backdrop-blur-md border border-white/10 rounded-[24px] transition-all duration-300 group-hover:border-cyan-500/50 group-hover:-translate-y-2"
                >
                    <div
                        class="absolute top-0 right-0 w-12 h-12 border-t-2 border-r-2 border-cyan-500/0 group-hover:border-cyan-500/50 transition-all rounded-tr-[24px]"
                    ></div>

                    <p
                        class="font-mono text-[10px] text-cyan-500/70 mb-4 tracking-[0.2em]"
                    >
                        DATA_STREAM_{ev.id}
                    </p>

                    <h3
                        id={`ev-${ev.id}-title`}
                        class="text-2xl font-bold text-white mb-2 tracking-tight group-hover:text-cyan-400 transition-colors"
                    >
                        {ev.title}
                    </h3>

                    <div class="flex items-center gap-2 mb-6">
                        <span
                            class="px-2 py-0.5 rounded bg-cyan-500/10 text-cyan-400 text-[10px] font-mono border border-cyan-500/20"
                        >
                            {ev.date}
                        </span>
                    </div>

                    <p
                        class="text-slate-400 text-sm leading-relaxed font-light italic"
                    >
                        "{ev.summary}"
                    </p>

                    <div
                        class="absolute bottom-0 left-8 right-8 h-[1px] bg-gradient-to-r from-transparent via-cyan-500/50 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"
                    ></div>
                </div>
            </article>
        {/each}
    </div>
</div>

<style>
    /* Hide scrollbar for Chrome, Safari and Opera */
    .scrollbar-none::-webkit-scrollbar {
        display: none;
    }

    /* Hide scrollbar for IE, Edge and Firefox */
    .scrollbar-none {
        -ms-overflow-style: none; /* IE and Edge */
        scrollbar-width: none; /* Firefox */
    }
</style>
