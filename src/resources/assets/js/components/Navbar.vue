<template>
    <nav class="navbar navbar-expand-sm navbar-dark bg-info mb-2">
        <div class="container">
            <a href="#" class="navbar-brand">Larticles</a>
            <a v-if="!have_user" href="/login" class="navbar-brand">Login</a>
        </div>
    </nav>
</template>
<script>
export default {
    data(){
        return{
            have_user: false
        }
    },
    mounted() {
        this.getTokens();
    },
    methods: {
        getTokens() {
            axios.get('/oauth/clients')
                    .then(response => {
                        if(response.data[0]){
                            this.have_user=true;
                        }
                        else{
                            this.have_user=false;
                        }
                    });
        },
    }
}
</script>
