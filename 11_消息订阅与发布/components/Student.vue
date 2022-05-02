<template>
    <div class="student">
        <h2>{{name}}</h2>
        <h2>{{age}}</h2>
        <button @click="sendStudent">将名字发给学校</button>
    </div>

</template>

<script>
    import PubSub from 'pubsub-js'
    export default {
        data() {
            return {
                name: '陈小希',
                age: 16
            }
        },
        methods: {
            sendStudent() {
                PubSub.publish('hello', this.name)
            }
        },

    }
</script>

<style>
    .student {
        background-color: orange;
        padding: 10px;
        margin: 10px;
    }
</style>