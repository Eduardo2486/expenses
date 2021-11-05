<script>
    import {onMount, onDestroy, beforeUpdate, afterUpdate} from 'svelte';
    onMount( ()=> {
        console.log("Form has mounted");
    });
    beforeUpdate( ()=> {
        console.count("Form before update");
    });
    afterUpdate( ()=> {
        console.count("Form  after update");
    }); 
    onDestroy( ()=> {
        console.log("Form has destroyed");
    });
    import Title from './Title.svelte';
    export let name = "";
    export let amount = null;
    export let isEditing;
    export let addExpense;
    export let editExpense;
    export let hideForm;
    $: isEmpty = !name || !amount;
    function handleSubmit(){
        if(isEditing){
            editExpense({name,amount});
        }else{
            addExpense({name,amount});
        }
        name="";
        amount=null;
        hideForm();
    }
    
    
</script>

<section class="form">
    <Title title="add expense"/>
    <form  class="expense-form" on:submit|preventDefault={handleSubmit}>
        <div class="form-control">
            <label for="name">name</label>
            <input type="text" id="name" bind:value={name}>
        </div>
        <div class="form-control">
            <label for="amount">amount</label>
            <input type="number" id="amount" bind:value={amount}>
        </div>
        {#if isEmpty}
            <p class="form-empty">
                Please fill out all fills
            </p>
        {/if}

        <button class="btn btn-block" type="submit" disabled={isEmpty} class:disabled={isEmpty}>
            {#if isEditing}
                edit expense
            {:else}
                add expense
            {/if}
        </button>

        <button type="button" class="close-btn" on:click={()=>hideForm()}>
            close
        </button>
    </form>
</section>