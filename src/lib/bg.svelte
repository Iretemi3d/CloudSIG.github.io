<script lang="ts">
    
    import { SVG, type Svg } from "@svgdotjs/svg.js";
    
    function add_path(
        draw: Svg,
        line1: string,
        _line2: string,
        delay: number,
        _dur: number
    ) {
        draw.size("100%", "100%");
        const path = draw
            .path(line1)
            .fill("none")
            .stroke({ width: 3, color: "#15e4ffff" });
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

<!-- Animated background lines -->
<div
    class="fixed top-0 right-0 bottom-0 left-0 z-[-2] opacity-60"
    id="drawing"
></div>

<!-- Radial gradient overlay -->
<div
    class="fixed top-0 right-0 bottom-0 left-0 z-[-1] filter pointer-events-none"
></div>