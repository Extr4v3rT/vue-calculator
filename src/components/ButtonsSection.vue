<template>
    <div class="buttons-section">
        <Button text="AC" buttonOrange @click="resultClear" />
        <Button text="<-" buttonOrange @click="deleteLastNumber" />
        <Button text="%" buttonOrange @getButtonValue="getButtonValue" />
        <Button text="/" buttonOrange @getButtonValue="getButtonValue" />
        <Button text="7" @getButtonValue="getButtonValue" />
        <Button text="8" @getButtonValue="getButtonValue" />
        <Button text="9" @getButtonValue="getButtonValue" />
        <Button text="*" buttonOrange @getButtonValue="getButtonValue" />
        <Button text="4" @getButtonValue="getButtonValue" />
        <Button text="5" @getButtonValue="getButtonValue" />
        <Button text="6" @getButtonValue="getButtonValue" />
        <Button text="-" buttonOrange @getButtonValue="getButtonValue" />
        <Button text="1" @getButtonValue="getButtonValue" />
        <Button text="2" @getButtonValue="getButtonValue" />
        <Button text="3" @getButtonValue="getButtonValue" />
        <Button text="+" buttonOrange @getButtonValue="getButtonValue" />
        <Button text=":)" buttonOrange />
        <Button text="0" @getButtonValue="getButtonValue" />
        <Button text="," @getButtonValue="getButtonValue" />
        <Button text="=" buttonOrange @click="getResult"/>
    </div>
</template>

<script>
import Button from './Button.vue'

import { evaluate } from 'mathjs'

export default {
    name: 'ButtonSection',
    props: {
        result: [String, Number],
    },
    components: {
        Button,
    },
    data: function() {
        return {
            math: 0,
        }
    },
    methods: {
        getButtonValue(e) {
            if(this.math == "Cannot divide by zero") {
                this.resultClear();
            }
            if(this.math == 0 && e.target.value != "%"
            && e.target.value != "/" && e.target.value != "*" && e.target.value != "-"
            && e.target.value != "+") {
                this.math = e.target.value;
            } else {
                this.math = this.math + e.target.value;
            }

            this.$emit('mathCalc', this.math);
        },
        resultClear() {
            this.$emit('resultClear', 0);
            this.math = 0;
        },
        deleteLastNumber() {
            this.math = Number(this.math.toString().split('').slice(0, -1).join(''))
            this.$emit('result', evaluate(this.math));
        },
        getResult() {
            if(this.math.includes("/0") ) {
                this.math = "Cannot divide by zero";
                const Obj = {
                    text: this.math,
                    type: "divideZero",
                }
                this.$emit('result', Obj);
            } else {
                this.math = evaluate(this.math);
                this.$emit('result', evaluate(this.math));
            }
        }
    },
}
</script>

<style scoped>
.buttons-section {
    height: calc(70% - 25px);
    width: 100%;
    padding: 20px;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
    text-align: center;
    align-items: center;
}
</style>