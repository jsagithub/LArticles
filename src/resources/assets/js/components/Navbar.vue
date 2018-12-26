<template>
    <nav class="navbar navbar-expand-sm navbar-dark bg-info mb-2">
        <div class="container">
            <a href="#" class="navbar-brand">Larticles</a>
            <a v-if="!haveLogin" href="/login" class="navbar-brand">Login</a>
            <a v-if="haveLogin" class="navbar-brand">{{userInfo['name']}}</a>
        </div>
    </nav>
</template>
<script>
export default {
    data () {
        return {
            userInfo: {},
            haveLogin: false
        }
    },
    created() {
            axios.get('/api/user')
            .then(res => {          
                if(res){
                    this.userInfo = res.data;  
                    this.haveLogin = true;    
                }
            })
            .catch(err => {
                this.haveLogin = false;
                console.log(err);
            });
    }
}
</script>
