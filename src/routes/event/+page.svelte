
<script lang="ts">

    import Bg from "$lib/bg.svelte";
    import EventsScroller from "$lib/eventsScroller.svelte";
    import Foot from "$lib/foot.svelte";
</script>

<Bg/>


<div class="min-h-40"></div>

<div class="max-w-[85%] mx-auto padding">
    <h1 class="text-6xl text-highlight space font-whatever">Events</h1>

    <div class="min-h-30"></div>

     <div class="mx-auto max-w-[80%] base-1/10 backdrop-blur-sm border border-accent pl-10 pr-10 rounded-3xl">
        <h1 class="text-4xl text-highlight pt-15 pb-10" style="font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;"> Welcome event to Cloud SIG</h1>
        <p class="description-text">
        CLOUDSIG IS BACK ☁️☁️☁️ <br>
        Cloudsig is back and eager to help you start out with Cloud!
        <br>
        Come Join Us
        We will help you get started, developing real Cloud skills to help you in future jobs and projects.
<br>
We will run our first Intro to Cloud workshop on the 20th of January from 6pm-8.30pm! 
<br>
We’ll demystify the Cloud for you and help you deploy a website to the Cloud. This will be hosted at 40 George Square
        </p>
        <br>
        <br>



        <!-- <a href="https://www.instagram.com/cloudsig_uoe">Instagram</a>
        <a href="https://www.linkedin.com/company/edinburgh-cloudsig/">LinkedIn</a>
        <a href="https://discord.gg/sEG7eUzjCk">Discord</a> -->

    </div>
    
     <div class="min-h-30"></div>

     <div class="mx-auto max-w-[80%] base-1/10 backdrop-blur-sm border border-accent pl-10 pr-10 rounded-3xl">
        <h1 class="text-4xl text-highlight p-20" style="font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;">Coming soon...</h1>
    </div>

   
</div>



<style>
    
    .description-text, p {
        font-size: clamp(1rem, 2vw, 1.25rem);
        line-height: 1.8;
        color: rgba(var(--color-accent-rgb, 255, 255, 255),1);
        font-weight: 400;
    }
    a{
        font-size: clamp(1rem, 2vw, 1.25rem);
        color:rgb(187, 22, 238);

    }
</style>