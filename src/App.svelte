<script>
    import { tweened } from "svelte/motion";
    import { cubicOut } from "svelte/easing";

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
</script>

<progress value={$progress} />
<Spring />
