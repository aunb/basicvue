<template>


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
                                        <td>{{p.name.split(",")}}</td>
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
    </div>
    <!-- ============================================================== -->
    <!-- End Page wrapper  -->
    <!-- ============================================================== -->

</template>

<script>

import axios from 'axios';
export default {
    name: 'ContactUs',
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
