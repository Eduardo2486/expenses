<script>
    import SectionTitle from './Title.svelte';
    import Expense from './Expense.svelte';
    export let expenses = [];
    import {fly} from 'svelte/transition';
    import {flip} from 'svelte/animate';
</script>

<section>
    <SectionTitle title='Expense List' />
    <ul>
        {#each expenses as expense, index (expense.id)}
            <div in:fly={{x:200, delay:index*200}} out:fly={{x:-200}} animate:flip>
                <Expense {...expense} />
            </div>
        {:else}
            <h2>Currently you have no expenses</h2>
        {/each}
    </ul>
</section>