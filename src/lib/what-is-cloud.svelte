<script>
    import Aws from "$lib/assets/aws.png";
    import Azure from "$lib/assets/azure.png";
    import Debian from "$lib/assets/debian.png";
    import Fedora from "$lib/assets/fedora.png";
    import Github from "$lib/assets/github.png";
    import Kubernetes from "$lib/assets/kubernetes.png";
</script>

<div class="bg-base-1 pt-10 mt-10">
    <div class="container">
        <div class="grid-layout">
            <div class="text-section">
                <h1 class="text-4xl text-highlight font-titles animate-fadeIn">
                    What is Cloud?
                </h1>
                <p class="text-2xl text-highlight">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Sequi deserunt eum officia suscipit totam velit ea illum
                    autem eligendi, ducimus doloremque dolorum qui cupiditate
                    assumenda, perspiciatis sunt aspernatur maxime ad. Lorem
                    ipsum dolor, sit amet consectetur adipisicing elit. Minus
                    nobis delectus atque commodi, iste aspernatur quisquam dicta
                    quod id culpa, fugiat odit nisi adipisci? Libero sunt rem
                    autem aspernatur sint.
                </p>
            </div>

            <div class="images-section">
                <img src={Aws} alt="AWS" class="floating-image bg-white" />
                <img src={Azure} alt="Azure" class="floating-image" />
                <img src={Debian} alt="Debian" class="floating-image" />
                <img src={Fedora} alt="Fedora" class="floating-image" />
                <img
                    src={Github}
                    alt="GitHub"
                    class="floating-image bg-white"
                />
                <img src={Kubernetes} alt="Kubernetes" class="floating-image" />
            </div>
        </div>
    </div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&family=Stack+Sans+Text:wght@200..700&display=swap");

    .bg-base-1 {
        background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        min-height: 100vh;
    }

    .container {
        max-width: 1400px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    .grid-layout {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 4rem;
        align-items: center;
    }

    .text-section {
        padding: 3rem;
    }

    .font-titles {
        font-family: "Momo Trust Display", sans-serif;
    }

    .text-4xl {
        font-size: 3.5rem;
        margin-bottom: 2rem;
    }

    .text-2xl {
        font-size: 1.25rem;
        line-height: 1.8;
    }

    .text-highlight {
        color: var(--color-accent);
    }

    .text-section p {
        color: var(--color-accent);
    }

    .animate-fadeIn {
        animation: fadeIn 1s ease-in;
    }

    .images-section {
        position: relative;
        height: 600px;
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
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    }

    .floating-image:hover {
        transform: scale(1.2) rotate(5deg);
        box-shadow: 0 16px 48px var(--color-accent);
    }

    .floating-image:nth-child(1) {
        top: 10%;
        left: 15%;
        animation: float 6s ease-in-out infinite;
    }

    .floating-image:nth-child(2) {
        top: 5%;
        right: 20%;
        animation: float 7s ease-in-out infinite 1s;
    }

    .floating-image:nth-child(3) {
        top: 35%;
        left: 5%;
        animation: float 8s ease-in-out infinite 2s;
    }

    .floating-image:nth-child(4) {
        top: 40%;
        right: 10%;
        animation: float 6.5s ease-in-out infinite 1.5s;
    }

    .floating-image:nth-child(5) {
        bottom: 25%;
        left: 25%;
        animation: float 7.5s ease-in-out infinite 0.5s;
    }

    .floating-image:nth-child(6) {
        bottom: 20%;
        right: 25%;
        animation: float 8.5s ease-in-out infinite 2.5s;
    }

    .floating-image:nth-child(7) {
        bottom: 5%;
        left: 45%;
        animation: float 7s ease-in-out infinite 3s;
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
            transform: translateY(0px);
        }
        50% {
            transform: translateY(-20px);
        }
    }

    @media (max-width: 1024px) {
        .grid-layout {
            grid-template-columns: 1fr;
            gap: 2rem;
        }

        .images-section {
            height: 400px;
        }

        .floating-image {
            width: 80px;
            height: 80px;
            padding: 1rem;
        }
    }
</style>
