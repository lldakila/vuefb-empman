<template>
    <nav>
        <div class="nav-wrapper red lighten-2">
            <div class="container">
                <router-link to="/" class="brand-logo">
                    EmpMan
                </router-link>
                <a href="#" data-target="mobile-demo" class="sidenav-trigger"><i class="material-icons">menu</i></a>
                <!-- <a href="#" data-target="#mobile-demo" class="sidenav-trigger"><i class="material-icons">menu</i></a> -->
                <ul class="right hide-on-med-and-down">
                    <li v-if="isLoggedIn">
                        <span class="email black-text">
                            {{currentUser}}
                        </span>
                    </li>
                    <li v-if="isLoggedIn">
                        <router-link to="/">Dashboard</router-link>
                    </li>
                    <li v-if="!isLoggedIn">
                        <router-link to="/login">Login</router-link>
                    </li>
                    <li v-if="!isLoggedIn">
                        <router-link to="/register">Register</router-link>
                    </li>
                    <li v-if="isLoggedIn">
                        <button class="btn black white-text" v-on:click="logout">Logout</button>
                    </li>
                    <li>
                        <a href="https://lldakila.github.io" target="blank">About Dakila</a>
                    </li>
                </ul>

                <ul class="sidenav" id="mobile-demo">
                    <li v-if="isLoggedIn">
                        <span class="email black-text">
                            {{currentUser}}
                        </span>
                    </li>
                    <li v-if="isLoggedIn">
                        <router-link to="/">Dashboard</router-link>
                    </li>
                    <li v-if="!isLoggedIn">
                        <router-link to="/login">Login</router-link>
                    </li>
                    <li v-if="!isLoggedIn">
                        <router-link to="/register">Register</router-link>
                    </li>
                    <!-- <li v-if="isLoggedIn">
                        <a class="btn black" v-on:click="logout">Logout</a>
                    </li> -->
                    <li v-if="isLoggedIn">
                        <a class="white-text black" v-on:click="logout">Logout</a>
                    </li>
                    <li>
                        <a href="lldakila.github.io">About Dakila</a>
                    </li>
                </ul>

                <div class="sidenav-overlay" style="display: none; opacity: 0;"></div>
                <div class="drag-target"></div>
            </div>
        </div>
    </nav>
</template>

<script>
// document.addEventListener('DOMContentLoaded', function() {
//     var elems = document.querySelectorAll('.sidenav');
//     var instances = M.Sidenav.init(elems);
//   });

    
import firebase from 'firebase';
export default {
    name: 'navbar',
    data(){
        return{
            isLoggedIn: false,
            currentUser: false
        }
    },
    created(){
        if(firebase.auth().currentUser){
            this.isLoggedIn = true
            this.currentUser = firebase.auth().currentUser.email
        }
    },
    methods:{
        logout: function(){
            firebase.auth().signOut()
                .then(() => {
                    // this.$router.push('/login');
                    this.$router.go({ path: this.$router.path });
            });
        }
    },
    mounted() {
        $(document).ready(function(){
        $('.sidenav').sidenav();
        })
    }
    
}


</script>

<style scoped>
.email{
    padding-right: 10px;
    padding-left: 10px;
}
</style>
