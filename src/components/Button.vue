<template>
    <div class="button__container" v-on:click="this.show" >
        <button class="button" :value="this.text" v-on:click="onClick" v-bind:class="{ 'button--orange': this.buttonOrange }" >
        {{text}}
        </button>
    </div>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        buttonOrange: Boolean
    },
    data: function() {
        return {
            tekstt: this.text,
        }
    },
    methods: {
        onClick(e) {
            this.$emit('getButtonValue', e);
        }
    }
}
</script>

<style>
.button__container {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
        user-select: none;
    -webkit-user-select: none;
}
.button {
    width: 50px;
    height: 50px;
    border-radius:100%;
    background-color: white;
    color: black;
    display:flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 0px 15px 5px rgba(0,0,0,0.5);
    background-color: #2b4663;
    color:white;
    font-family: Roboto;
    font-weight: bold;
    font-size: 1.5rem;
    user-select: none;
    -webkit-user-select: none;
    -webkit-tap-highlight-color: transparent;
    cursor:pointer;
    outline: none;
}
.button--orange {
    background-color: red;
}
</style>