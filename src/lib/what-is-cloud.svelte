<script>
    import Aws from "$lib/assets/aws.png";
    import Azure from "$lib/assets/azure.png";
    import Debian from "$lib/assets/debian.png";
    import Fedora from "$lib/assets/fedora.png";
    import Github from "$lib/assets/github.png";
    import Kubernetes from "$lib/assets/kubernetes.png";

    let iconPositions = $state([
        { src: Aws, alt: "AWS", top: 40, left: 20 },
        { src: Azure, alt: "Azure", top: 15, left: 45 },
        { src: Debian, alt: "Debian", top: 25, left: 15 },
        { src: Fedora, alt: "Fedora", top: 60, left: 80 },
        { src: Github, alt: "GitHub", top: 75, left: 35 },
        { src: Kubernetes, alt: "K8s", top: 25, left: 75 },
    ]);

    let show_shuffle_button = $state(true);

    function shuffleIcons() {
        const minDistance = 20;
        let newPositions = [];
        iconPositions.forEach((icon) => {
            let randomTop,
                randomLeft,
                tooClose,
                attempts = 0;
            do {
                randomTop = Math.floor(Math.random() * 70) + 15;
                randomLeft = Math.floor(Math.random() * 70) + 15;
                tooClose = newPositions.some((pos) => {
                    const dist = Math.sqrt(
                        Math.pow(randomTop - pos.top, 2) +
                            Math.pow(randomLeft - pos.left, 2),
                    );
                    return dist < minDistance;
                });
                attempts++;
            } while (tooClose && attempts < 50);
            newPositions.push({ ...icon, top: randomTop, left: randomLeft });
        });
        iconPositions = newPositions;
    }
</script>

<section
    class="relative min-h-screen flex items-center justify-center bg-[#030712] overflow-hidden py-20 px-4"
>
    <div
        class="absolute inset-0 z-0 opacity-10"
        style="background-image: linear-gradient(#1e293b 1px, transparent 1px), linear-gradient(90deg, #1e293b 1px, transparent 1px); background-size: 50px 50px;"
    ></div>

    <div
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[500px] bg-cyan-500/10 blur-[160px] rounded-full"
    ></div>

    <div class="relative z-10 max-w-7xl w-full">
        <div
            class="relative backdrop-blur-2xl bg-slate-900/40 rounded-[40px] p-8 md:p-16 border border-white/10 shadow-[0_0_50px_rgba(0,0,0,0.5)]"
        >
            <div class="flex flex-col lg:flex-row items-center gap-12">
                <div class="lg:w-5/12 space-y-8">
                    <div
                        class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-cyan-500/30 bg-cyan-500/5 text-cyan-400 text-xs font-mono uppercase tracking-widest"
                    >
                        <span
                            class="w-2 h-2 rounded-full bg-cyan-400 animate-pulse"
                        ></span>
                        System Online
                    </div>

                    <h1
                        class="text-6xl md:text-8xl font-bold tracking-tighter leading-none"
                    >
                        <span class="text-white">What is</span><br />
                        <span
                            class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-500"
                            >Cloud?</span
                        >
                    </h1>

                    <p
                        class="text-slate-400 text-lg md:text-xl leading-relaxed font-light"
                    >
                        There is no fluffy cloud in the Cloud, it’s just
                        <span class="text-white font-medium italic"
                            >someone else’s computer.</span
                        >
                        Optimize your time, scale your infrastructure, and master
                        the digital sky.
                    </p>

                    <div class="flex flex-wrap gap-5 pt-4">
                        <button
                            class="px-8 py-4 bg-cyan-400 hover:bg-cyan-300 text-slate-950 font-bold rounded-2xl transition-all hover:scale-105 hover:shadow-[0_0_30px_rgba(34,211,238,0.4)]"
                        >
                            Start Workshop
                        </button>
                        <button
                            onclick={shuffleIcons}
                            class="px-8 py-4 bg-transparent hover:bg-white/5 text-white border border-white/20 rounded-2xl transition-all"
                        >
                            Reorganize Stack
                        </button>
                    </div>
                </div>

                <div class="lg:w-7/12 w-full h-[500px] relative">
                    <div
                        class="relative w-full h-full"
                        onclick={shuffleIcons}
                        role="presentation"
                    >
                        {#each iconPositions as icon}
                            <div
                                class="absolute transition-all duration-1000 ease-[cubic-bezier(0.23,1,0.32,1)]"
                                style="top: {icon.top}%; left: {icon.left}%; transform: translate(-50%, -50%);"
                            >
                                <div
                                    class="absolute inset-0 bg-cyan-400/20 blur-2xl rounded-full scale-150"
                                ></div>

                                <div class="relative group cursor-pointer">
                                    <div
                                        class="w-24 h-24 md:w-24 md:h-24 bg-white rounded-full flex items-center justify-center shadow-xl transition-transform duration-300 group-hover:scale-110"
                                    >
                                        <img
                                            src={icon.src}
                                            alt={icon.alt}
                                            class="w-12 h-12 md:w-12 md:h-12 object-contain"
                                        />
                                    </div>

                                    <div
                                        class="absolute -bottom-10 left-1/2 -translate-x-1/2 opacity-0 group-hover:opacity-100 transition-opacity bg-slate-900 text-[10px] text-cyan-400 font-mono px-2 py-1 rounded border border-cyan-500/30 whitespace-nowrap pointer-events-none"
                                    >
                                        {icon.alt}
                                    </div>
                                </div>
                            </div>
                        {/each}
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<style>
    :global(body) {
        background-color: #030712;
        margin: 0;
        font-family: sans-serif;
    }
</style>
