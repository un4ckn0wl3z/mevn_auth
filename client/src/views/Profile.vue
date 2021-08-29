<template>
    <div>
        <h2>Profile Page</h2>
        <div class="card" v-if="user">
            <ul class="list-group">
                <li class="list-group-item">Email: {{user.email}}</li>
                <li class="list-group-item">Username: {{user.username}}</li>
                <li class="list-group-item">Name: {{user.name}}</li>
            </ul>
        </div>
    </div>
</template>


<script>
import { mapGetters, mapActions } from 'vuex'
export default {
    computed: {
        ...mapGetters(['user'])
    },
    methods: {
        ...mapActions(['getProfile'])
    },
    created(){
        this.getProfile()
    }
};
</script>

<style>

</style>
