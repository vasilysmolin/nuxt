<template>
    <section class="container">
        <div>
            <h1 class="title">
                {{ user.name }}
            </h1>
            <h3>{{user.email}}</h3>
        </div>
    </section>
</template>

<script>
    export default {
        data: () => ({
            user: []
        }),
        async asyncData( { $axios,params } ) {
            const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/' + params.id)
            return {user}
        },
        validate({params}) {
            return /^\d+$/.test(params.id)
        }

    }
</script>