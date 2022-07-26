<script>
    import { tweened } from "svelte/motion";
    import { cubicOut } from "svelte/easing";
    import { fade, fly, slide, scale } from "svelte/transition";

    import Spring from "./Spring.svelte";

    // configuration for the tweened function
    const progress = tweened(0, {
        delay: 0,
        duration: 1000,
        easing: cubicOut,
        loop: true,
    });

    setTimeout(() => {
        progress.set(1);
    }, 1000);

    let boxes = ["Apples"];
    let boxInput;

    function addBox() {
        boxes = [...boxes, boxInput.value];
    }

    function discard(value) {
        boxes = boxes.filter((box) => box !== value);
    }
</script>

<!-- <progress value={$progress} />
<Spring /> -->

<input type="text" bind:this={boxInput} />
<button on:click={addBox}>Add</button>

{#each boxes as box (box)}
    <div
        on:click={discard.bind(this, box)}
        transition:fly={{
            delay: 0,
            duration: 400,
            easing: cubicOut,
            opacity: 0.5,
            x: -100,
            y: -100,
        }}
    >
        {box}
    </div>
{/each}

<style>
    div {
        width: 10rem;
        height: 10rem;
        background: #ccc;
        margin: 1rem;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        border-radius: 5px;
        padding: 16px;
    }
</style>
