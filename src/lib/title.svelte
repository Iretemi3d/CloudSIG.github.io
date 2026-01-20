<script lang="ts">
    import Icon from "$lib/assets/favicon.png";
</script>

<div class="h-20"></div>

<div class="relative px-4">
    <div
        class="group relative mx-auto max-w-5xl rounded-[40px] p-[1px] overflow-hidden bg-white/10 transition-all duration-500 shadow-[0_0_50px_rgba(34,211,238,0.15)]"
    >
        <div
            class="absolute inset-[-1000%] animate-[spin_6s_linear_infinite] bg-[conic-gradient(from_90deg_at_50%_50%,#00c2ff_0%,#15e4ff_50%,#00c2ff_100%)] opacity-0 group-hover:opacity-100 transition-opacity duration-500"
        ></div>

        <div
            class="relative backdrop-blur-2xl bg-slate-950/90 rounded-[39px] px-10 py-16 border border-white/5 overflow-hidden"
        >
            <div
                class="absolute inset-0 opacity-10 pointer-events-none"
                style="background-image: radial-gradient(#1e293b 1px, transparent 1px); background-size: 20px 20px;"
            ></div>

            <div
                class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-cyan-500/10 blur-[80px] rounded-full pointer-events-none group-hover:bg-cyan-500/20 transition-colors"
            ></div>

            <div class="relative z-10 flex flex-col items-center">
                <div
                    class="max-w-[200px] w-full aspect-square overflow-hidden relative mb-8"
                >
                    <img
                        src={Icon}
                        alt="Cloud SIG Logo"
                        class="crop-effect group-hover:scale-110 transition-transform duration-700"
                    />
                </div>

                <div class="w-full text-center">
                    <span
                        class="text-cyan-400 font-mono text-xs tracking-[0.3em] uppercase mb-4 block"
                        >Special Interest Group</span
                    >
                    <h1
                        class="text-6xl sm:text-9xl font-bold tracking-tighter animate-fadeIn text-transparent bg-clip-text bg-gradient-to-b from-white via-white to-slate-500"
                    >
                        Cloud SIG
                    </h1>
                </div>
            </div>
        </div>
    </div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&display=swap");

    /* Custom Animation for the Fade-In */
    .animate-fadeIn {
        animation: fadeIn 1.2s cubic-bezier(0.22, 1, 0.36, 1);
    }

    @keyframes fadeIn {
        from {
            opacity: 0;
            transform: translateY(20px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* Refined Crop effect to match your original intent but smoother */
    .crop-effect {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: contain;
        /* Matches your 15% top/bottom inset */
        clip-path: inset(15% 0 15% 0);
        filter: drop-shadow(0 0 15px rgba(21, 228, 255, 0.2));
    }

    :global(body) {
        background-color: #030712;
    }
</style>
