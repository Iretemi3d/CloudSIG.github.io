<script lang="ts">
  export interface EventCard {
    id: number;
    title: string;
    date: string;
    summary: string;
  }

  export let events: EventCard[] = [
    { id: 1, title: 'Intro to Cloud', date: 'Jan 12, 2026', summary: 'Kickoff session covering basics of cloud models.' },
    { id: 2, title: 'Serverless Night', date: 'Feb 03, 2026', summary: 'Deep dive into FaaS patterns and cost optimizations.' },
    { id: 3, title: 'Kubernetes Workshop', date: 'Mar 21, 2026', summary: 'Hands-on cluster setup and deployment pipelines.' },
    { id: 4, title: 'Data & AI', date: 'Apr 10, 2026', summary: 'Cloud data platforms and ML workflow integration.' },
    { id: 5, title: 'Edge Computing', date: 'May 05, 2026', summary: 'Latency reduction strategies and edge architectures.' }
  ];

  let scroller: HTMLDivElement | null = null;
  let isDragging = false;
  let startX = 0;
  let scrollStart = 0;

  function scrollByCards(direction: 1 | -1) {
    if (!scroller) return;
    const card = scroller.querySelector('.card') as HTMLElement | null;
    const amount = card ? card.offsetWidth + parseFloat(getComputedStyle(scroller).gap || '0') : 300;
    scroller.scrollBy({ left: direction * amount, behavior: 'smooth' });
  }

  
  function handleWheel(e: WheelEvent) {
    if (!scroller) return;
    // Use vertical wheel to scroll horizontally; support trackpads
    const delta = Math.abs(e.deltaY) > Math.abs(e.deltaX) ? e.deltaY : e.deltaX;
    scroller.scrollBy({ left: delta, behavior: 'auto' });
  }

  function startDrag(e: PointerEvent) {
    if (!scroller) return;
    isDragging = true;
    startX = e.clientX;
    scrollStart = scroller.scrollLeft;
    scroller.setPointerCapture(e.pointerId);
  }
  function onDrag(e: PointerEvent) {
    if (!isDragging || !scroller) return;
    const dx = e.clientX - startX;
    scroller.scrollLeft = scrollStart - dx; // content follows pointer
  }
  function endDrag(e: PointerEvent) {
    if (!isDragging || !scroller) return;
    isDragging = false;
    scroller.releasePointerCapture(e.pointerId);
  }
</script>

<section class="events-wrapper" aria-label="Upcoming events">
  <div class="controls">
    <button type="button" class="nav" on:click={() => scrollByCards(-1)} aria-label="Scroll left">◄</button>
    <button type="button" class="nav" on:click={() => scrollByCards(1)} aria-label="Scroll right">►</button>
  </div>

  <div
    bind:this={scroller}
    class="scroller {isDragging ? 'dragging' : ''}"
    tabindex="0"
    on:wheel|preventDefault={handleWheel}
    on:pointerdown={startDrag}
    on:pointermove={onDrag}
    on:pointerup={endDrag}
    on:pointerleave={endDrag}
  >
    {#each events as ev}
      <article class="card" aria-labelledby={`ev-${ev.id}-title`}>
        <h3 id={`ev-${ev.id}-title`} class="card-title">{ev.title}</h3>
        <p class="card-date">{ev.date}</p>
        <p class="card-summary">{ev.summary}</p>
      </article>
    {/each}
  </div>
</section>

<style>
  .events-wrapper {
    position: relative;
    width: 100%;
    margin: 0 auto;
    padding: 0 10px 30px;
  }
  .controls {
    display: flex;
    justify-content: flex-end;
    gap: 8px;
    margin-bottom: 10px;

  }
  .nav {
    background: var(--color-base-2, #222);
    color: var(--color-accent);
    border: 1px solid var(--color-accent);
    padding: 6px 12px;
    font-size: 15px;
    cursor: pointer;
    border-radius: 6px;
    transition: background .2s;
    width: 5%;
  }
  .nav:hover, .nav:focus { background: var(--color-accent); color: #000; }

  .scroller {
    display: flex;
    gap: 20px;
    overflow-x: auto;
    overscroll-behavior-x: contain;
    scroll-snap-type: x mandatory;
    scrollbar-width: none; /* Firefox */
    padding: 10px 5px 10px 5px;
    cursor: grab;
    user-select: none;
    -ms-overflow-style: none; /* IE/Edge legacy */
    touch-action: pan-y pinch-zoom; /* retain vertical gestures for nested areas */
  }
  .scroller:focus {outline-offset: 2px; }
  .scroller::-webkit-scrollbar { display: none; }
  .scroller.dragging { cursor: grabbing; }

  .card {
    flex: 0 0 280px;
    scroll-snap-align: start;
    background: rgba(0,0,0,0.4);
    backdrop-filter: blur(4px);
    border: 1px solid var(--color-accent);
    border-radius: 12px;
    padding: 16px 18px 20px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    color: var(--color-highlight);
    min-height: 50%;
    min-width: 10%;
  }
  .card-title { font-size: 150%; margin: 0; }
  .card-date { font-size: 80%; opacity: 0.8; margin: 0; color: var(--color-accent);}
  .card-summary { font-size: 120%; margin: 0; }

  @media (min-width: 900px) {
    .card { flex-basis: 320px; }
  }
</style>
