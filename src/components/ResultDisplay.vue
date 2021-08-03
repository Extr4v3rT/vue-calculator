<template>
    <div class="result-display">
        <!-- <input type="text" class="result-display__input" v-model="this.result" disabled> -->
        <p class="result-display__input">{{math}}</p>
    </div>
</template>

<script>
export default {
    name: 'ResultDisplay',
    props: {
        result: Number,
        math: [Number, String]
    },
    data: function() {
        return {
            
        }
    }
}
</script>

<style scoped>
.result-display {
    width: 100%;
    height: 30%;
    background-color: #192e44;
    display: flex;
    align-items: flex-end;
    border-bottom: 3px solid black;
}
.result-display__input {
    width: 100%;
    height:50%;
    background-color: #192e44;
    color: white;
    font-family: Roboto;
    font-size: 40px;
    text-align: right;
    border: none;
    padding: 0 10px;
    margin: 0;
}
</style>