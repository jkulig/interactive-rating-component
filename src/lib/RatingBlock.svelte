<script>
    import { createEventDispatcher } from 'svelte';
    import { selectedRating } from './stores.js';

    let selected;
    const ratings = [1, 2, 3, 4, 5];
    let error = false;

    const dispatch = createEventDispatcher();

    selectedRating.subscribe(value => {
        selected = value;
    })

    function handleClick(evt) {
        selectedRating.set(parseInt(evt.target.dataset.value));
        error = false;
    }

    function handleSubmit() {
        (selected && selected > 0) ? onSuccess() : handleError();
    }

    function onSuccess() {
        dispatch('success');
    }

    function handleError() {
        error = true;
    }

</script>

<div class="ratings">
    {#each ratings as rating}
        <button class:rating class:selected={selected === rating} data-value={rating} on:click={handleClick}>{rating}</button>
    {/each}
</div>

<button class="submit" on:click={handleSubmit}>
  Submit
</button>

{#if error}
    <div class:error>Please rate before submitting</div>
{/if}


<style>
    .ratings {
        display: flex;
        justify-content: space-between;
        margin-bottom: 30px;
    }

    .rating {
        display: block;
        width: 50px;
        height: 50px;
        line-height: 50px;
        border-radius: 50%;
        text-align: center;
        background-color: var(--dark-blue);
        border: none;
        font-size: 18px;
        color: var(--medium-grey);
    }

    .rating:hover {
        background-color: var(--primary-color);
        color: white;
        cursor: pointer;
    }
    
    .rating.selected {
        background-color: var(--light-grey);
        color: white;        
    }

    .submit {
        border: none;
        width: 100%;
        height: 50px;
        border-radius: 25px;
        background-color: var(--primary-color);
        color: white;
        text-transform: uppercase;
        letter-spacing: 3px;
        font-weight: 700;
        font-size: 1rem;
        cursor: pointer;
    }

    .submit:hover,
    .submit:focus {
        background-color: white;
        color: var(--primary-color);
    }

    .error {
        color: red;
        text-align: center;
        margin-top: 10px;
    }
</style>