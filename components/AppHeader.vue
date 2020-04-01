<template>
    <nav class="navbar" role="navigation">
        <div class="navbar-brand">
            <a role="button" data-target="navbarList" class="navbar-burger burger" v-on:click="toggleBurger()" v-bind:class="{'is-Active': isActive}">
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
            </a>
        </div>
        <div id="navbarList" class="navbar-menu" v-bind:class="{'is-active' : isActive}">
            <div class="navbar-end">
                <a class="navbar-item">
                    <nuxt-link to="/">Home</nuxt-link>
                </a>
                <a class="navbar-item">
                    <nuxt-link to="/jokes">Jokes</nuxt-link>
                </a>
                <a class="navbar-item">
                    <nuxt-link to="/about">About</nuxt-link>
                </a>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'AppHeader',
    data(){
        return {
            isActive: false
        }
    },
    methods: {
        toggleBurger(){
            this.isActive = !this.isActive
        }
    }
}
</script>