<template>
<!-- ============================================================== -->
<!-- Main wrapper - style you can find in pages.scss -->
<!-- ============================================================== -->
<div id="main-wrapper" data-layout="vertical" data-navbarbg="skin6" data-sidebartype="full" data-sidebar-position="absolute" data-header-position="absolute" data-boxed-layout="full">
    <!-- ============================================================== -->
    <!-- Topbar header - style you can find in pages.scss -->
    <!-- ============================================================== -->
    <header class="topbar" data-navbarbg="skin6">
        <nav class="navbar top-navbar navbar-expand-md navbar-dark">
            <div class="navbar-header background-color">
                <!-- ============================================================== -->
                <!-- Logo -->
                <!-- ============================================================== -->
                <a class="navbar-brand ms-4" href="http://127.0.0.1:8000/home">
                    <!-- Logo text -->
                    <span class="logo-text">
                        <!-- dark Logo text -->
                        <img src="http://127.0.0.1:8000/assets/peoplei.png" alt="homepage" class="dark-logo" />
                    </span>
                </a>
                <!-- ============================================================== -->
                <!-- End Logo -->
                <!-- ============================================================== -->
                <!-- ============================================================== -->
                <!-- toggle and nav items -->
                <!-- ============================================================== -->
                <a class="
                        nav-toggler
                        waves-effect waves-light
                        text-white
                        d-block d-md-none
                      " href="javascript:void(0)"><i class="ti-menu ti-close"></i></a>
            </div>
            <!-- ============================================================== -->
            <!-- End Logo -->
            <!-- ============================================================== -->
            <div class="navbar-collapse collapse" id="navbarSupportedContent" data-navbarbg="skin5">
                <!-- ============================================================== -->
                <!-- Right side toggle and nav items -->
                <!-- ============================================================== -->
                <ul class="navbar-nav ml-auto">
                    <!-- ============================================================== -->
                    <!-- User profile and search -->
                    <!-- ============================================================== -->
                    <li class="nav-item dropdown">
                        <a class="
                            nav-link
                            dropdown-toggle
                            text-muted
                            waves-effect waves-dark
                          " href="http://127.0.0.1:8000/home" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                            People Tech
                        </a>
                        <ul class="dropdown-menu" aria-labelledby="navbarDropdown"></ul>
                    </li>
                </ul>
            </div>
        </nav>
    </header>

    <!-- ============================================================== -->
    <!-- End Topbar header -->
    <!-- ============================================================== -->
    <!-- ============================================================== -->
    <!-- Left Sidebar - style you can find in sidebar.scss  -->
    <!-- ============================================================== -->
    <aside class="left-sidebar" data-sidebarbg="skin6">
        <SidebarView />
    </aside>
    <!-- ============================================================== -->
    <!-- End Left Sidebar - style you can find in sidebar.scss  -->
    <!-- ============================================================== -->
    <!-- ============================================================== -->
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
                                            <input type="text" class="form-control" placeholder="User Name" name="name" v-model="name">
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
    <!-- ============================================================== -->
    <!-- End Page wrapper  -->
    <!-- ============================================================== -->
</div>
 
</template>

<script>
import SidebarView from "./common/SideBar.vue"
import axios from "axios";
export default {
    name: "ContactUs",
    components: {
        SidebarView
    },
    data() {
        return {
            isLoading: false,
            name: "",
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
