<script lang="ts">
    import "./layout.css";
    import favicon from "$lib/assets/favicon.png";
    import Nav from "$lib/nav.svelte";
    import Foot from "$lib/foot.svelte";
    

    let { children } = $props();
</script>

<svelte:head>
    <link rel="icon" href={favicon} />
</svelte:head>

<div
    class="min-h-screen min-w-screen fixed left-0 top-0 -z-50 bg-radial from-base-2 from-0% to-base-1 to-100%"
></div>

<Nav />


{@render children()}


