<template>
    <div>
        <nav id="navbar-example2" class="navbar navbar-light bg-light">
            <a class="navbar-brand" href="#">Nuxt ssr</a>
            <ul class="nav nav-pills">
                <li class="nav-item">
                    <nuxt-link exact active-class="active" class="nav-link" to="/">
                        home
                    </nuxt-link>
                </li>
                <li class="nav-item">
                    <nuxt-link active-class="active" class="nav-link" to="/about">
                        about
                    </nuxt-link>
                </li>
                <li class="nav-item">
                    <nuxt-link active-class="active" class="nav-link" to="/users">
                        users
                    </nuxt-link>
                </li>
                <li class="nav-item" v-if="!hasToken">
                    <nuxt-link active-class="active" class="nav-link" to="/login">
                        login
                    </nuxt-link>
                </li>
                <li class="nav-item" v-else>
                    <a @click.prevent="logout"  class="nav-link">logout</a>
                </li>
            </ul>
        </nav>
    </div>
</template>
<script>
    export default {
        computed: {
            hasToken() {
                return this.$store.getters.hasToken
            }
        },
        methods: {
            logout() {
                this.$store.dispatch('logout')
                this.$router.push('/login')
            }
        }
    }
</script>