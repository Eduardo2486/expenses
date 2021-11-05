<script>
    import {blur,fade,fly} from 'svelte/transition';
</script>

<div class="modal-container" in:blur out:fade>
    <div class="modal-content" transition:fly={{duration:200}}>
        <slot>Hello modal</slot>
    </div>
</div>