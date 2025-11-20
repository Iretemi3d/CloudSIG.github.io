<nav
    class="flex items-center fixed left-0 top-0 bg-base-1/95 w-full px-6 py-3 shadow-md z-40 border-b border-accent/30"
>
    <div class="flex-1 flex items-center">
        <a
            href="/"
            class="text-accent font-semibold text-lg transition-transform hover:scale-125 ease-in-out duration-500"
            >Cloud SIG</a
        >
    </div>

    <div class="flex-1 flex justify-end">
        <div class="flex items-center space-x-4">
            <a
                href="/about"
                class="text-highlight text-sm px-3 py-2 rounded transition-colors hover-line"
                >About</a
            >
            <a
                href="/sponsors"
                class="text-highlight text-sm px-3 py-2 rounded transition-colors hover-line"
                >Sponsors</a
            >
            <a
                href="/event"
                class="text-highlight text-sm px-3 py-2 rounded transition-colors hover-line"
                >Events</a
            >
        </div>
    </div>
</nav>

<style>
    .hover-line {
        position: relative;
        display: inline-block;
        padding-bottom: 3px;
    }

    .hover-line::before {
        content: "";
        position: absolute;
        left: 10%;
        right: 10%;
        bottom: 0;
        height: 2px;
        width: 0;
        background-color: var(--color-accent);
        transition: width 200ms ease-in-out;
    }

    .hover-line:hover::before {
        width: 80%;
    }
</style>
