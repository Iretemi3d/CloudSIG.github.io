<script lang="ts">
    import Title from "$lib/title.svelte";
    import { SVG, type Svg } from "@svgdotjs/svg.js";
    import EventsScroller from "$lib/eventsScroller.svelte";

    function add_path(
        draw: Svg,
        line1: string,
        _line2: string,
        delay: number,
        _dur: number
    ) {
        draw.size("100%", "100%");

        //"#1EDF9555"
        const path = draw
            .path(line1)
            .fill("none")
            .stroke({ width: 3, color: "#ffc815" });
        const length = path.length();

        // @ts-ignore
        path.stroke({
            dasharray: length,
            dashoffset: length,
        });

        path.animate(1000, delay).ease("<>").stroke({ dashoffset: 0 });

        return path;
    }

    $effect(() => {
        let draw = SVG().addTo("#drawing");
        add_path(
            draw,
            "M 0 300 C 673 651 922 1 2000 370",
            "M 0 300 C 622 471 661 -303 2000 211",
            0,
            3000
        );
        add_path(
            draw,
            "M 0 591 C 676 148 731 766 2000 211",
            "M 0 591 C 600 616 731 607 2000 411",
            200,
            3500
        );
        add_path(
            draw,
            "M 0 100 C 873 651 722 -171 2071 700",
            "M 0 100 C 629 651 484 402 2071 565",
            400,
            4500
        );
    });
</script>

<div class="fixed top-0 right-0 bottom-0 left-0 z-[-2]" id="drawing"></div>
<div class="fixed top-0 right-0 bottom-0 left-0 z-[-1] filter"></div>

<Title />

<div class="max-w-[85%] mx-auto padding">
    <h1 class="text-4xl text-highlight space font-titles animate-fadeIn">What is Cloud?</h1>
    <p class="text-2xl text-highlight space" style="padding-top: 0px;">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Sequi deserunt
        eum officia suscipit totam velit ea illum autem eligendi, ducimus
        doloremque dolorum qui cupiditate assumenda, perspiciatis sunt
        aspernatur maxime ad. Lorem ipsum dolor, sit amet consectetur
        adipisicing elit. Minus nobis delectus atque commodi, iste aspernatur
        quisquam dicta quod id culpa, fugiat odit nisi adipisci? Libero sunt rem
        autem aspernatur sint.
    </p>
</div>


<div class="max-w-[85%] mx-auto padding">
    <h1 class="text-4xl text-highlight space font-titles">Events</h1>
    <EventsScroller />
</div>





<style>
    .filter {
        background: radial-gradient(
            circle at center,
            transparent 0%,
            var(--color-base-1) 95%,
            var(--color-base-1) 100%
        );
    }

    .space {
        padding: 50px;
        
    }
    .padding {
        padding-top: 70px;
    }
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&family=Stack+Sans+Text:wght@200..700&display=swap");
    .font-titles {
        font-family: "Momo Trust Display", sans-serif;
    }


</style>
