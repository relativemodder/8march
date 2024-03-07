<script lang="ts">
    import compliments from '$lib/data';
    import { fly } from 'svelte/transition';

    let linkPlaceholder = "#";

    let index = $state(0);

    function onNext() {
        index++;
        if (index == compliments.length) {
            index = 0;
        }
    }
</script>

<div class="fixed top-10 flex justify-center w-full">
    <h2>Relative's March 8th app</h2>
</div>

<div class="fixed bottom-10 flex justify-center w-full">
    <a 
        on:click|preventDefault={onNext}
        class="bg-green-600 text-white 
        font-bold text-4xl min-w-96 p-5 
        text-center rounded-xl
        active:bg-green-700
        shadow-xl shadow-green-950" 
        href={linkPlaceholder}
    >
        Yes!
    </a>
</div>

<div class="flex w-full h-screen justify-center items-center">
    <div class="
        border-solid border-2 
        min-w-96 h-44 border-slate-800 
        p-5 rounded-xl
        shadow-md shadow-gray-950"
    >
    <div class="w-full h-full">
        <h1 class="text-6xl text-center font-extrabold">Are you...</h1>
        <div class="mt-10">
        {#each compliments as compliment, i}
            { #if i == index }
                <h2 class="text-2xl text-center font-semibold absolute left-0 w-full overflow-hidden" 
                transition:fly={{duration: 500, opacity: 0, x: -100}}>
                    { compliment.icon } { compliment.text }?
                </h2>
            { /if }
        { /each }
        </div>
        <h1> </h1>
    </div>
    </div>
</div>  
