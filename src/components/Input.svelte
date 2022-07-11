<script>
    export let value = '';
</script>

<fieldset>
    <div class="form-group">
        <input class="form-control" {...$$restProps} bind:value />
    </div>
</fieldset>

<style>
    input {
        max-width: 200px;
    }

    /* Chrome, Safari, Edge, Opera */
    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    /* Firefox */
    input[type='number'] {
        -moz-appearance: textfield;
    }

    input::placeholder {
        font-size: small;
    }
</style>
