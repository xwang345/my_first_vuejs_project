<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <button v-on:click="onClickMe">Click!</button>
    </div>
</template>

<script>
export default {
    data () {
        return {
            msg: 'Hello from component a!'
        }
    },
    props: ['msgfromparent'],
    method: {
        onClickMe () {
            console.log(this.msgfromparent)
        }
    }
}
</script>

<style>
    /* h1{
        color: red;
    } */
</style>

