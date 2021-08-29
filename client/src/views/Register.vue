<template>
    <div>
        <h2>Register</h2>
        <div class="row">
            <div class="card mx-auto">
                <div class="card-header text-white bg-primary mt-2">
                    <h4>Register</h4>
                </div>
                <div class="card-body">
                    <form @submit.prevent="registerUser">
                        <div class="form-group">
                            <label for="name">Name</label>
                            <input id="name" type="text" placeholder="Name" name="name" v-model="name" class="form-control">
                        </div>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input id="email" type="email" placeholder="Email" name="email" v-model="email" class="form-control">
                        </div>                                                  
                        <div class="form-group">
                            <label for="username">Username</label>
                            <input id="username" type="text" placeholder="Username" name="username" v-model="username" class="form-control">
                        </div>
                        <div class="form-group">
                            <label for="password">Password</label>
                            <input id="password" type="password" placeholder="Password" name="password" v-model="password" class="form-control">
                        </div>
                        <div class="form-group">
                            <label for="confirm_password">Confirm password</label>
                            <input id="confirm_password" type="password" placeholder="Confirm password" name="confirm_password" v-model="confirm_password" class="form-control">
                        </div>                        
                        <input type="submit" class="btn btn-primary" value="Register">
                        &nbsp;&nbsp;&nbsp;&nbsp;
                        <router-link to="/login" class="card-link">Already have an account?</router-link>                       
                    </form>
                </div>
            </div>
        </div>        
    </div>
</template>


<script>
import { mapActions } from 'vuex'

export default {
    data() {
        return {
            username: "",
            password: "",
            name: "",
            email: "",
            confirm_password: ""
        }
    },
    methods: {
        ...mapActions(['register']),
        registerUser(){
            let user = {
                username: this.username,
                password: this.password,
                name: this.name,
                email: this.email,
                confirm_password: this.confirm_password                
            }
            this.register(user).then(res => {
                if(res.data.success){
                    this.$router.push("/login")
                }
            })
        }

    }
}
</script>

<style>
.card {
    width: 60%;
    border-radius: 0;
}
.btn {
    border-radius: 0;
}
.form-control {
    border-radius: 0;
}
</style>

