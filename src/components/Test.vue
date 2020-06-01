<template>
    <nav>
    <div class="nav-wrapper green">
        <div class="container">
            <router-link to="/" class="brand-logo">
                Employee Manager
            </router-link>
            <a href="#" data-target="#mobile-demo" class="sidenav-trigger"><i class="material-icons">menu</i></a>
            <ul class="right hide-on-med-and-down">
                <li>
                    <router-link to="/login">Login</router-link>
                </li>
                <li>
                    <router-link to="/register">Register</router-link>
                </li>
            </ul>
        </div>
    </div>
    <ul class="sidenav" id="mobile-demo">
        <li>
            <router-link to="/login">Login</router-link>
        </li>
        <li>
            <router-link to="/register">Register</router-link>
        </li>
</ul>
    </nav>

    

</template>

<script>
export default {
    name: 'test',
    data(){
        return{
        }
    }

    
}
  $(document).ready(function(){
    $('.sidenav').sidenav();
  });
</script>
