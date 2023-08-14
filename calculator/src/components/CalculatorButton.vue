<template>
    <button class="calculator-button"
        @click="$emit('onClick', label)"
        :class="{ double, triple, operation }">
        {{ label }}
    </button>
</template>

<script>
export default {
    props: {
        label: {},
        operation: { type: Boolean },
        double: { type: Boolean },
        triple: { type: Boolean }
    }
}
</script>

<style>
:root {
    --bg-button: #f0f0f0;
    --border-button: solid 1px #888;
}

.calculator-button {
    font-size: 1.4em;
    background-color: var(--bg-button);
    border: none;
    border-right: var(--border-button);
    border-bottom: var(--border-button);
    outline: none;
}

.calculator-button:active {
    background-color: #ccc;
}

.calculator-button.double {
    grid-column: span 2;
}

.calculator-button.triple {
    grid-column: span 3;
}

.calculator-button.operation {
    background-color: #fa8231;
    color: #fff;
}

.calculator-button.operation:active {
    background-color: #fa8231cc;
}
</style>