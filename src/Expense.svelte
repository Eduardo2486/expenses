<script>    
    import { getContext } from 'svelte';
    import { slide, scale, fade, fly, blur } from 'svelte/transition';
    export let name;
    export let amount;
    export let id ;
    let displayAmount = false;

    function toggleAmount(){
        displayAmount = !displayAmount ;
    }
    const removeExpense = getContext('remove');
    const modifyExpense = getContext('modify');
</script>

<article class="single-expense" style="border:1px solid #000;">
    <div class="expense-info">
        <h2>
            {name}
            <button class="amount-btn" on:click={toggleAmount}>
                >
            </button>
        </h2>
        {#if displayAmount}
            <h4 in:fly={{x:100,y:100,duration:2000,delay:500}} out:slide>amount: {amount}</h4>
        {/if}
    </div>
    <div class="expense-buttons">
        <button class="expense-btn edit-btn" on:click={()=>modifyExpense(id)}>
            Edit
        </button>
        <button class="expense-btn delete-btn" on:click={()=>removeExpense(id)}>
            Delete
            
        </button>
    </div>
</article>