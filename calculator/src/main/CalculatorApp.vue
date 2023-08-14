<template>
    <div class="calculator">
        <CalculatorDisplay :value="displayValue" />
        <CalculatorButton label="AC" triple @onCLick="clearMemory" />
        <CalculatorButton label="/" operation @onCLick="setOperation" />
        <CalculatorButton label="7" @onCLick="addDigit" />
        <CalculatorButton label="8" @onCLick="addDigit" />
        <CalculatorButton label="9" @onCLick="addDigit" />
        <CalculatorButton label="*" operation @onCLick="setOperation" />
        <CalculatorButton label="4" @onCLick="addDigit" />
        <CalculatorButton label="5" @onCLick="addDigit" />
        <CalculatorButton label="6" @onCLick="addDigit" />
        <CalculatorButton label="-" operation @onCLick="setOperation" />
        <CalculatorButton label="1" @onCLick="addDigit" />
        <CalculatorButton label="2" @onCLick="addDigit" />
        <CalculatorButton label="3" @onCLick="addDigit" />
        <CalculatorButton label="+" operation @onCLick="setOperation" />
        <CalculatorButton label="0" double @onCLick="addDigit" />
        <CalculatorButton label="." @onCLick="addDigit" />
        <CalculatorButton label="=" operation @onCLick="setOperation" />
    </div>
</template>

<script>
import CalculatorButton from '../components/CalculatorButton.vue';
import CalculatorDisplay from '../components/CalculatorDisplay.vue';

export default {
    data: function() {
        return {
            displayValue: '0',
            clearDisplay: false,
            operation: null,
            values: [0, 0],
            current: 0
        }
    },
    components: { CalculatorButton, CalculatorDisplay },
    methods: {
        clearMemory() {
            Object.assign(this.$data, this.$options.data())
        },

        setOperation(operation) {
            
        },
        
        addDigit(n) {
            if (n === "." && this.displayValue.includes(".")) {
                return
            }

            const clearDisplay = this.displayValue === "0" || this.clearDisplay
            const currentValue = clearDisplay ? "" : this.displayValue
            const displayValue = currentValue + n

            this.displayValue = displayValue
            this.clearDisplay = false

            if (n !== ".") {
                const i = this.current
                const newValue = parseFloat(displayValue)
                this.values[i] = newValue
            }
        }
    }
}
</script>

<style>
.calculator {
    height: 320px;
    width: 235px;
    border-radius: 5px;
    overflow: hidden;

    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>