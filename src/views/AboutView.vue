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
                            <table class="table table-bordered">
                                <thead>
                                    <tr>
                                        <th scope="col">#</th>
                                        <th scope="col">User Name</th>
                                        <th scope="col">Email</th>
                                        <th scope="col">image</th>
                                        <th scope="col">Edit</th>
                                        <th scope="col">Delete</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <p v-if="isLoading">Loading...</p>
                                    <tr v-else v-for="p in users" :key="p.id">
                                        <td>{{p.id}} </td>
                                        <td>{{p.name}}</td>
                                        <td>{{p.email}}</td>
                                        <td><img v-bind:src="p.image" style="height:20px;width:20px"/> </td>
                                        <td><router-link :to="{ path: '/edit-user/'+p.id}">Edit</router-link></td>
                                        <td><a href="#" v-on:click="deleteData(p.id)" style="color:red">Delete</a></td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <!-- ============================================================== -->
        <!-- End Container fluid  -->
        <!-- ============================================================== -->
        <!-- ============================================================== -->

        <!-- ============================================================== -->
    </div>
    <!-- ============================================================== -->
    <!-- End Page wrapper  -->
    <!-- ============================================================== -->
</div>
</template>

<script>
import SidebarView from "./common/SideBar.vue"
import axios from 'axios';
export default {
    name: 'ContactUs',
    components: {
        SidebarView
    },
    data() {
        return {
            users: [],
            isLoading: false
        }
    },
    methods: {
        getPosts() {
            this.isLoading = true
            axios.get('http://127.0.0.1:8000/api/users')
                .then(response => response)
                .then(response => {
                    this.users = response.data;
                    this.isLoading = false
                });
        },
        deleteData: function (id) {
          let x = window.confirm("You want to delete the user?");
          if(x){
               axios.delete('http://127.0.0.1:8000/api/user/delete/' + id)
                .then(response => response)
                .then(response => {
                    if (response) {
                        this.getPosts();
                    }

                });
          }
        },
    },
    mounted() {
        this.getPosts()
    }
}
</script>
