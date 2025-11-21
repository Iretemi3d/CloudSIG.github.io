<script lang="ts">
    import Icon from "$lib/assets/favicon.png";
</script>

<div class="h-20"></div>

<div>
    <div
        class="mx-auto max-w-[80%] base-1/10 backdrop-blur-sm border border-accent pl-10 pr-10 rounded-3xl"
    >
        <div class="max-w-md mx-auto aspect-square overflow-hidden relative imgeffect">
            <img
                src={Icon}
                alt="THIS IS SUPPOSED TO BE THE ICON"
                class="crop-bottom-80 hover:animate-pulse"
                
            />
        </div>

        <div class="w-full text-center pb-10">
            <h1 class="text-5xl sm:text-8xl text-highlight font-whatever animate-fadeIn">
                Cloud SIG
            </h1>
        </div>
    </div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=BBH+Sans+Hegarty&family=Momo+Trust+Display&display=swap");

    .font-whatever {
        font-family: "BBH Sans Hegarty", monospace;
    }

    .crop-bottom-80 {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: bottom;
        clip-path: inset(15% 0 15% 0);
    }
    
</style>
