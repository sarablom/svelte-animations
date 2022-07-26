<script>
    import { writeable } from "svelte/store";
    const progress = writeable(0);
</script>

<progress value={$progress}></progress>

