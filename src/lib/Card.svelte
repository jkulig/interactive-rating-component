<script>
    export let summary = false;
</script>

<div class="card-container" class:summary={summary}>
    <slot></slot>
</div>

<style>
    .card-container {
        background: radial-gradient(circle at top, rgba(36,41,53,1) 0%, rgba(24,30,40,1) 100%);
        max-width: 330px;
        padding: 30px;
        border-radius: 25px;
        display: flex;
        flex-direction: column;
        align-items: stretch;
    }

    .summary {
        align-items: center;
        text-align: center;
    }
</style>