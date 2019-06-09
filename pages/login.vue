<template>
    <section>
        <h1>Login</h1>
        <form @click.prevent="onSubmit">
            <div class="form-groupe">
                <input type="text" class="form-control">
            </div>
            <button class="btn btn-primary" type="submit">Login</button>
        </form>
    </section>
</template>

<script>
    export default {
        layout: 'empty',
        methods: {
            onSubmit() {
                this.$store.dispatch('login')
                this.$router.push('/')
            }
        }
    }
</script>