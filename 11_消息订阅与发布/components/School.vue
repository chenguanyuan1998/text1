<template>
    <div class="school">
        <h2>{{schoolname}}</h2>
        <h2>{{adress}}</h2>
    </div>
</template>

<script>
    import pubsub from 'pubsub-js'
    export default {
        name: 'School',
        data() {
            return {
                schoolname: '广东工业大学',
                adress: "广州市番禺区大学城"
            }
        },
        methods: {
            demo(data) {
                console.log('我是学校，我收到了学生的姓名', data);
            }
        },
        mounted() {
            this.pid = pubsub.subscribe('hello', this.demo);
        },
        beforeDestroy() {
            pubsub.unsubscribe(this.pid)
        },

    }
</script>

<style>
    .school {
        background-color: yellow;
        padding: 10px;
        margin: 10px;
    }
</style>