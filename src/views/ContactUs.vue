<template>
    <!-- Page wrapper  -->
    <!-- ============================================================== -->
    <div class="page-wrapper">
        <div class="container-fluid">
            <div class="row justify-content-center">
                <div class="col-md-6">
                    <div class="card">
                        <div class="card-body p-5">
                            <form class="input-feild" @submit.prevent="handleSubmit">
                                <input type="hidden" name="_token" value="2DaJkqJmyx0DSJyZ887cap1jWperaJjEWGfkRdio">
                                <div class="row">
                                    <div class="col-md-12">
                                        <div class="form-group">
                                            <input type="checkbox" value="aa" name="name[]" v-model="name">ssss
                                            <input type="checkbox" value="aas" name="name[]" v-model="name">ssss
                                            <input type="checkbox" value="aab" name="name[]" v-model="name">ssss
                                            <input type="checkbox" value="aad" name="name[]" v-model="name">ssss
                                        </div>
                                    </div>
                                    <div class="col-md-12">
                                        <div class="form-group">
                                            <input type="email" class="form-control" placeholder="Email" name="email" v-model="email">
                                        </div>
                                    </div>
                                </div>
                                <div class="row">
                                    <div class="col-md-12">
                                        <div class="form-group">
                                            <input type="file" class="form-control" name="image" v-on:change="onImageChange">
                                        </div>
                                    </div>
                                    <div class="col-md-12">
                                        <div class="form-group">
                                            <input type="password" class="form-control" placeholder="Password" name="password" v-model="password">
                                        </div>
                                    </div>
                                </div>

                                <button type="submit" class="btn btn-primary float-right">Submit</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <!-- ============================================================== -->
        <!-- End Container fluid  -->
        <!-- ============================================================== -->
        <!-- ============================================================== -->
        <!-- footer -->
        <!-- ============================================================== -->
     
        <!-- ============================================================== -->
        <!-- End footer -->
        <!-- ============================================================== -->
    </div>
  
</template>

<script>
import axios from "axios";
export default {
    name: "ContactUs",
    data() {
        return {
            isLoading: false,
            name: [],
            email: "",
            image: '',
            password: "",
        };
    },
    methods: {
        onImageChange(e){
                console.log(e.target.files[0]);
                this.image = e.target.files[0];
        },
        
        handleSubmit() {
            const config = {
                headers: { 'content-type': 'multipart/form-data' }
            }
            this.isLoading = true;
            axios.post("http://127.0.0.1:8000/api/user/create",{
                    name: this.name,
                    email: this.email,
                    password: this.password,
                    image: this.image
                    },
                    config
                )
                .then(() => {
                    // this.name = "";
                    // this.email = "";
                    // this.password = "";
                    this.isLoading = false;
                });
        },
    },
};
</script>
