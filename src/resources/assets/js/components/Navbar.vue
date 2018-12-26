<template>
    <nav class="navbar navbar-expand-sm navbar-dark bg-info mb-2">
        <div class="container">
            <a href="#" class="navbar-brand">Larticles</a>
            <a v-if="!userInfo" href="/login" class="navbar-brand">Login</a>
            <a v-if="userInfo" class="navbar-brand">{{userInfo['name']}}</a>
        </div>
    </nav>
</template>
<script>
export default {
    data () {
        return {
            userInfo: {}
        }
    },
    created() {
            axios.get('/api/user')
            .then(res => {          
                this.userInfo = res.data;      
            })
            .catch(err => console.log(err));
    }
}
</script>
