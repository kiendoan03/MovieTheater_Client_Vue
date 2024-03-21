<template>
      <section class="col-3">
                <a href="/">
                    <img class="col-4" src="../assets/image/NetFnix Full logo.png" alt="">
                </a>
            </section>

            <section class="col-3 d-flex justify-content-end pe-3">

                <div class=" position-relative border border-0 me-2 rounded-circle text-center" style="height: 3vmax; width: 3vmax; background-color: #ffffff48;">
                    <i class="fa-regular fa-bell position-absolute top-50 start-50 translate-middle" style="font-size: 1.2vmax;color: #ffffff"></i>
                </div>

                <div class="position-relative border border-0 me-2 rounded-circle text-center" style="height: 3vmax; width: 3vmax; background-color: #ffffff48;">
                    <a href="#">
                        <i class="fa-solid fa-magnifying-glass position-absolute top-50 start-50 translate-middle" style="font-size: 1.2vmax;color: #ffffff"></i>
                    </a>
                </div>

                    <div class="dropdown">
                        <img class="col-12 border" style="border-radius: 50%;object-fit: cover; overflow: hidden;height: 3vmax; width: 3vmax;" src="../assets/image/Netflix-avt.png" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false" height="" alt="">
                            <ul class="dropdown-menu bg-dark" aria-labelledby="dropdownMenuButton1"> 
                                <li><RouterLink v-if="!auth" class="dropdown-item bg-dark text-light" to="/login">Login</RouterLink></li>
                                <li><Button v-if="auth" @click="logout" class="dropdown-item bg-dark text-light">Logout</Button></li>
                            </ul>
                    </div>  

            </section>
</template>
<script>
    export default {
        name: 'HeaderView',
        data: function() {
        return {
            auth: false,
        }
    },
    mounted() {
        this.auth = localStorage.getItem('role') == 'Customer' && localStorage.getItem('token') != null;
        console.log(this.auth);
    },
    methods: {
        logout() {
            localStorage.removeItem('token');
            localStorage.removeItem('role');
            this.$router.push('/login');
        }
    }
}
</script>