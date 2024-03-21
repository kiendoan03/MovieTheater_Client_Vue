<template>
<div class="container-fluid">
        <div class="row mb-5 " style="padding-top:7em;">
            <div class="col-6 mx-auto">

                <h2 class="text-light text-center">Register</h2>
                <form method="post" class="" action="#">
                    <div class="mb-3">
                        <input class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="User name" name="username" style="outline: none;" required>
                    </div>
                   
                    <div class="mb-3">
                        <input type="text" class="border-0 border-bottom  col-12 py-3 bg-transparent text-white" placeholder="Full name" name="full_name" style="outline: none;" required>
                    </div>
                    <div class="mb-3">
                        <label for="dob" class="text-secondary">Date of birth</label>
                        <input type="date" class="border-0 border-bottom col-12 py-3 bg-transparent text-light" placeholder="Date of birth" name="date_of_birth" style="outline: none;" required>
                    </div>
                    <div class="mb-3">
                        <input type="email" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Email" name="cus_email" style="outline: none;" required>
                    </div>
                    
                    <div class="mb-3">
                        <input type="text" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Address" name="cus_address" style="outline: none;" required>
                    </div>
                    <div class="mb-3">
                        <input type="text" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Phonenumber" name="cus_phonenumber" style="outline: none;" required>
                    </div>
                   
                    <div class="mb-3">
                        <input type="password" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Password" name="password" style="outline: none;" required>
                    </div>
                    <div class="mb-3">
                        <input type="password" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Re-password" name="re_password" style="outline: none;" required>
                    </div>
                   

                    <button type="submit" name="register_btn" class="mb-2 text-dark py-3 mt-3 col-12 border-0 bg-transparent login__button position-relative">
                            <div class="text-light fs-5">Register</div>
                        </button>
                    <RouterLink class="text-decoration-danger fs-6 text-danger fw-light fst-italic" to="/login">Already have an account?</RouterLink>

                </form>
            </div>

        </div>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>

</style>