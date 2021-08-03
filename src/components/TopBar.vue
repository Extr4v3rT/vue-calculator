<template>
    <div class="top-bar">
        <div class="top-bar__icon top-bar__icon--close"></div>
        <div class="top-bar__icon top-bar__icon--full-window"></div>
        <div class="top-bar__icon top-bar__icon--minimalize"></div>
    </div>
</template>

<script>
export default {
    name: 'TopBar'
}
</script>

<style scoped>
.top-bar {
    height: 25px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;

    padding: 0 10px;
    background-color: #000e1d;
}
.top-bar__icon {
    width: 12px;
    height: 12px;
    border-radius: 100%;
    margin: 0 3px;
    filter: saturate(80%);
}
.top-bar__icon--minimalize {
    background-color: green;
}
.top-bar__icon--close {
    background-color: red;
}
.top-bar__icon--full-window {
    background-color: yellow;
}
</style>