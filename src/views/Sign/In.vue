<template>
    <div class="form">
        <div class="header">Login to the portal</div>
        <input v-model="email" type="text" placeholder="email address">
        <input v-model="password" type="password" placeholder="password">
        <button type="submit" class="btn" @click="submit()">
            LOGIN
        </button>
        <button class="btn signup" @click="$router.push('/sign/up')">
            GO TO SIGNUP
        </button>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data(){
        return {
            email: '',
            password: '' 
        }
    },
    methods: {
        submit() {
            if(!(this.email && this.password)){
                alert('fill the form')
                return
            }
            let _this = this
            axios({
                method: 'post',
                url: 'http://5.101.181.188:8085/auth/passenger/signin/',
                data: {
                    username: 'dake@gmail.com',
                    password: '123456'
                }
            }).then(function(response) {
                console.log(response)
                _this.$store.commit('setLogedIn', true)
                _this.$router.push('/profile');
            });
        }
    }
}
</script>

<style lang="scss" scoped>
    .signup{
        background-color: #fff !important;
        color: #fb7b4c !important;
        border: 1px solid #fb7b4c;
        border-radius: 3px;
    }
</style>