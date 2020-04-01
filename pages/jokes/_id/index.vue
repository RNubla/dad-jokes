<template>
    <div>
        <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
        <h2>{{joke}}</h2>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return {
            joke: {}
        }
    },
    async created(){
        const config = {
             headers: {
                 'Accept': 'application/json'
             }
        }
        try {
            const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`,config)
            console.log(res.data.joke)
            this.joke = res.data.joke
        } catch (error ) {
            console.log(error)
        }
    },
    head(){
        return{
            title: this.joke,
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'best place for corny dad jokes'
                }
            ]
        }
    }
}
</script>