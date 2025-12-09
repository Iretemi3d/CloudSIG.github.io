<script>
    import Aws from "$lib/assets/aws.png";
    import Azure from "$lib/assets/azure.png";
    import Debian from "$lib/assets/debian.png";
    import Fedora from "$lib/assets/fedora.png";
    import Github from "$lib/assets/github.png";
    import Kubernetes from "$lib/assets/kubernetes.png";

    function shuffleIcons() {
        const icons = [
            document.querySelector(".aws-icon"),
            document.querySelector(".azure-icon"),
            document.querySelector(".debian-icon"),
            document.querySelector(".fedora-icon"),
            document.querySelector(".github-icon"),
            document.querySelector(".k8s-icon"),
        ];

        const positions = [];
        const minDistance = 20; // minimum distance in percentage points

        icons.forEach((icon) => {
            if (icon) {
                let randomTop, randomLeft, tooClose;
                let attempts = 0;
                const maxAttempts = 100;

                do {
                    randomTop = Math.floor(Math.random() * 80) + 10; // 10% to 90%
                    randomLeft = Math.floor(Math.random() * 80) + 10; // 10% to 90%
                    tooClose = false;

                    // Check distance from all existing positions
                    for (let pos of positions) {
                        const distance = Math.sqrt(
                            Math.pow(randomTop - pos.top, 2) +
                                Math.pow(randomLeft - pos.left, 2)
                        );

                        if (distance < minDistance) {
                            tooClose = true;
                            break;
                        }
                    }

                    attempts++;
                } while (tooClose && attempts < maxAttempts);

                positions.push({ top: randomTop, left: randomLeft });
                icon.style.top = randomTop + "%";
                icon.style.left = randomLeft + "%";
            }
        });
    }
</script>

<section class="relative px-6 md:px-12 lg:px-20 py-16">
    <div
        class="max-w-7xl mx-auto backdrop-blur-sm bg-opacity-20 bg-white/5 rounded-2xl p-8 md:p-12 border border-white/10 shadow-2xl overflow-hidden"
    >
        <!-- Subtle background glow effect -->
        <div class="glow-orb glow-orb-1"></div>
        <div class="glow-orb glow-orb-2"></div>

        <div class="container">
            <div class="flex flex-col md:flex-row">
                <div class="text-section flex-6">
                    <h1 class="title-text font-titles animate-fadeIn">
                        What is Cloud?
                    </h1>
                    <p class="description-text">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Sequi deserunt eum officia suscipit totam velit ea illum
                        autem eligendi, ducimus doloremque dolorum qui
                        cupiditate assumenda, perspiciatis sunt aspernatur
                        maxime ad.
                    </p>
                    <p class="description-text mt-6">
                        Lorem ipsum dolor, sit amet consectetur adipisicing
                        elit. Minus nobis delectus atque commodi, iste
                        aspernatur quisquam dicta quod id culpa, fugiat odit
                        nisi adipisci? Libero sunt rem autem aspernatur sint.
                    </p>

                    <!-- Optional CTA button -->
                    <div class="mt-8">
                        <button class="cta-button">
                            Learn More
                            <svg
                                class="inline-block ml-2 w-5 h-5"
                                fill="none"
                                stroke="currentColor"
                                viewBox="0 0 24 24"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    stroke-width="2"
                                    d="M17 8l4 4m0 0l-4 4m4-4H3"
                                />
                            </svg>
                        </button>
                    </div>
                </div>

                <div class="images-section flex-4">
                    <div class="floating-container">
                        <img
                            src={Aws}
                            alt="AWS"
                            class="floating-image aws-icon"
                        />
                        <img
                            src={Azure}
                            alt="Azure"
                            class="floating-image azure-icon"
                        />
                        <img
                            src={Debian}
                            alt="Debian"
                            class="floating-image debian-icon"
                        />
                        <img
                            src={Fedora}
                            alt="Fedora"
                            class="floating-image fedora-icon"
                        />
                        <img
                            src={Github}
                            alt="GitHub"
                            class="floating-image github-icon"
                        />
                        <img
                            src={Kubernetes}
                            alt="Kubernetes"
                            class="floating-image k8s-icon"
                        />
                        <button
                            onclick={shuffleIcons}
                            class="cta-button opacity-20 hover:opacity-95"
                            style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); z-index: 100;"
                        >
                            Shuffle Icons
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<style>
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&family=Stack+Sans+Text:wght@200..700&display=swap");

    .container {
        max-width: 1400px;
        margin: 0 auto;
        position: relative;
        z-index: 1;
    }

    .grid-layout {
        display: grid;
        grid-template-columns: 1fr 1fr;
        align-items: center;
    }

    .text-section {
        padding: 2rem 0;
    }

    .font-titles {
        font-family: "Momo Trust Display", sans-serif;
    }

    .title-text {
        font-size: clamp(2.5rem, 5vw, 4rem);
        margin-bottom: 2rem;
        color: var(--color-accent);
        background: linear-gradient(
            135deg,
            #15e4ff 0%,
            #00c2ff 50%,
            #0099ff 100%
        );
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        line-height: 1.2;
        font-weight: 700;
        letter-spacing: -0.02em;
    }

    .description-text {
        font-size: clamp(1rem, 2vw, 1.25rem);
        line-height: 1.8;
        color: rgba(var(--color-accent-rgb, 255, 255, 255), 0.85);
        font-weight: 300;
    }

    .cta-button {
        padding: 1rem 2rem;
        background: linear-gradient(135deg, #15e4ff 0%, #0099ff 100%);
        color: #0a0e27;
        border: none;
        border-radius: 12px;
        font-size: 1.1rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        box-shadow: 0 8px 24px rgba(21, 228, 255, 0.3);
        display: inline-flex;
        align-items: center;
    }

    .cta-button:hover {
        transform: translateY(-3px);
        box-shadow: 0 12px 32px rgba(21, 228, 255, 0.5);
    }

    .cta-button:active {
        transform: translateY(-1px);
    }

    .animate-fadeIn {
        animation: fadeIn 1s ease-in;
    }

    .floating-container {
        position: relative;
        width: 100%;
        min-height: 600px;
    }

    .floating-image {
        position: absolute;
        width: 120px;
        height: 120px;
        object-fit: contain;
        border-radius: 20px;
        padding: 1.5rem;
        transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        cursor: pointer;
        box-shadow:
            0 8px 32px rgba(0, 0, 0, 0.3),
            0 0 0 1px rgba(255, 255, 255, 0.1);
        background: linear-gradient(
            135deg,
            rgba(255, 255, 255, 0.95) 0%,
            rgba(255, 255, 255, 0.9) 100%
        );
        backdrop-filter: blur(10px);
        transform: translate(-50%, -50%);
    }

    .floating-image:hover {
        transform: scale(1.15) rotate(5deg) translate(-50%, -50%);
        box-shadow:
            0 16px 48px rgba(21, 228, 255, 0.6),
            0 0 60px rgba(21, 228, 255, 0.4),
            0 0 0 1px rgba(21, 228, 255, 0.5);
        z-index: 10;
    }

    .aws-icon {
        top: 50%;
        left: 10%;
    }
    .azure-icon {
        top: 15%;
        left: 30%;
    }
    .debian-icon {
        top: 10%;
        left: 10%;
    }
    .fedora-icon {
        top: 50%;
        left: 70%;
    }
    .github-icon {
        top: 75%;
        left: 30%;
    }
    .k8s-icon {
        top: 15%;
        left: 70%;
    }

    .glow-orb {
        position: absolute;
        border-radius: 50%;
        filter: blur(80px);
        opacity: 0.15;
        pointer-events: none;
        z-index: 0;
    }

    .glow-orb-1 {
        width: 400px;
        height: 400px;
        background: #15e4ff;
        top: -100px;
        left: -100px;
        animation: pulse 8s ease-in-out infinite;
    }

    .glow-orb-2 {
        width: 350px;
        height: 350px;
        background: #0099ff;
        bottom: -100px;
        right: -100px;
        animation: pulse 10s ease-in-out infinite 2s;
    }

    @keyframes fadeIn {
        from {
            opacity: 0;
            transform: translateY(-20px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @keyframes float {
        0%,
        100% {
            transform: translateY(0px) rotate(0deg);
        }
        50% {
            transform: translateY(-20px) rotate(3deg);
        }
    }

    @keyframes pulse {
        0%,
        100% {
            transform: scale(1);
            opacity: 0.15;
        }
        50% {
            transform: scale(1.1);
            opacity: 0.25;
        }
    }

    @media (max-width: 1024px) {
        .grid-layout {
            grid-template-columns: 1fr;
            gap: 3rem;
        }

        .images-section {
            min-height: 450px;
        }

        .text-section {
            text-align: center;
        }

        .cta-button {
            margin: 0 auto;
        }
    }

    @media (max-width: 640px) {
        .images-section {
            min-height: 350px;
        }

        .floating-image {
            width: 70px;
            height: 70px;
            padding: 0.75rem;
        }

        .description-text {
            font-size: 1rem;
        }
    }
</style>
