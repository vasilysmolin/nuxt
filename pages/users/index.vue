<template>
    <section class="container">
        <div>
            <h1 class="title">
                users
            </h1>
            <ul>
                <li v-for="user of users" :key="user.id">
                    <a href="#" @click.prevent="openUser(user)">{{ user.name }}</a>

                </li>
            </ul>
        </div>
    </section>
</template>

<script>
    export default {
        // async asyncData( { $axios } ) {
        //     const users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
        //     return {users}
        // },
        async fetch ({store}) {
            if (store.getters['users/users'].length === 0) {
               await store.dispatch('users/fetch')
            }
        },
        computed: {
            users() {
                return this.$store.getters['users/users']
            }
        },
        // data: () => ({
        //    users: []
        // }),
        methods: {
            openUser(user) {
                this.$router.push('/users/' + user.id);
            }
        },
        // async mounted() {
        //     this.users = await this.$axios.$get('https://jsonplaceholder.typicode.com/users')
        // }
    }
</script>