<template>

    <!-- ============================================================== -->
    <!-- Main wrapper - style you can find in pages.scss -->
    <!-- ============================================================== -->
    <div id="main-wrapper" data-layout="vertical" data-navbarbg="skin6" data-sidebartype="full"
        data-sidebar-position="absolute" data-header-position="absolute" data-boxed-layout="full">
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
                            <img src="http://127.0.0.1:8000/assets/peoplei.png" alt="homepage"
                                class="dark-logo" />
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
                      "
                        href="javascript:void(0)"><i class="ti-menu ti-close"></i></a>
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
                          "
                                href="http://127.0.0.1:8000/home" id="navbarDropdown" role="button" data-bs-toggle="dropdown"
                                aria-expanded="false">
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

        <!-- Sidebar scroll-->
        <div class="scroll-sidebar">
            <!-- Sidebar navigation-->
            <nav class="sidebar-nav">
                <ul id="sidebarnav">
                    <!-- User Profile-->
                    <li class="sidebar-item">
                        <router-link class="sidebar-link waves-effect waves-dark sidebar-link" to="/"
                            aria-expanded="false"><span
                                class="hide-menu">Dashboard</span></router-link>
                    </li>
           
                    <!-- <li class="sidebar-item">
                        <a class="sidebar-link waves-effect waves-dark sidebar-link" href="http://127.0.0.1:8000/employees"
                            aria-expanded="false">
                            <i class="mdi me-2 mdi-account-check"></i><span class="hide-menu">Employees</span></a>
                    </li> -->
                    <li class="sidebar-item">
                        <router-link  class="sidebar-link waves-effect waves-dark sidebar-link" to="about"
                            aria-expanded="false">
                           <span class="hide-menu">About </span></router-link >
                    </li>
                        <li class="sidebar-item">
                        <router-link  class="sidebar-link waves-effect waves-dark sidebar-link" to="Contact-us"
                            aria-expanded="false">
                            <span class="hide-menu">Contact Us </span></router-link >
                    </li>
                    <li class="sidebar-item">
                        <a class="sidebar-link waves-effect waves-dark sidebar-link" href="pages-blank.html"
                            aria-expanded="false" onclick="event.preventDefault();
                            document.getElementById('logout-form').submit();"><span
                                class="hide-menu">Logout</span></a>
                        <form id="logout-form" action="http://127.0.0.1:8000/logout" method="POST" class="d-none">
                            <input type="hidden" name="_token" value="2DaJkqJmyx0DSJyZ887cap1jWperaJjEWGfkRdio">                    
                                </form>
                    </li>
                </ul>
            </nav>
            <!-- End Sidebar navigation -->
        </div>
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
                              <form action="http://127.0.0.1:8000/export-data" method="POST">
                                  <input type="hidden" name="_token" value="2DaJkqJmyx0DSJyZ887cap1jWperaJjEWGfkRdio">
                                  <div class="row">
                                                                  <p class="pl-3 pt-3">Source Database Detail</p> 
                                      <div class="col-md-6">
                                          <div class="form-group">
                                              <input type="text" class="form-control" placeholder="DB Host" name="db_host"  required>
                                          </div>
                                      </div>
                                      <div class="col-md-6">
                                          <div class="form-group">
                                              <input type="text" class="form-control" placeholder="DB Name" name="db_name" required>
                                          </div>
                                      </div>
                                  </div>
                                  <div class="row">
                                      <div class="col-md-6">
                                          <div class="form-group">
                                              <input type="text" class="form-control" placeholder="DB User" name="db_user" required>
                                          </div>
                                      </div>
                                      <div class="col-md-6">
                                          <div class="form-group">
                                              <input type="text" class="form-control" placeholder="DB Password" name="db_password">
                                          </div>
                                      </div>
                                  </div>
                                  <div class="row">
                                      <p class="pl-3 pt-3">Peoplei Detail</p> 
                                      <div class="col-md-12">
                                          <div class="form-group">
                                              <select class="form-select">
                                                  <option >Select Peoplei Version</option>
                                                  <option value="Peoplei 2.3.1">Peoplei 2.3.1</option>
                                              </select>
                                          </div>
                                      </div>
                                      <div class="col-md-12">
                                          <div class="form-group">
                                              <select class="form-select" name="module">
                                                  <option value="">Select Module</option>
                                                  <option value="Leave Applications">Leave Applications</option>
                                                  <option value="Leave Qouta">Leave Qouta</option>
                                                  <option value="Comp & Ben">Comp & Ben</option>
                                                  <option value="Expense">Expense</option>
                                                  <option value="Travel">Travel</option>
                                                  <option value="Loan Application">Loan Application</option>
                                                  <option value="MIS">MIS</option>
                                                  <option value="job Description">job Description</option>
                                                  <option value="Goal Settings">Goal Settings</option>
                                                  <option value="Competency Framework">Competency Framework</option>
                                                  <option value="Company Profile">Company Profile</option>
                                                  <option value="Company Bank Accounts">Company Bank Accounts</option>
                                                  <option value="Company Branches">Company Branches</option>
                                                  <option value="Appraisal Setting">Appraisal Setting</option>
                                                  <option value="Shift Setup">Shift Setup</option>
                                                  <option value="Increment Distribution">Increment Distribution</option>
                                                  <option value="Increment Budget">Increment Budget</option>
                                                  <option value="Appraisal History">Appraisal History</option>
                                              </select>
                                          </div>
                                      </div>
                                  </div>
                              
                                  <button type="submit" class="btn btn-primary float-right">Download Data</button>
                              </form>
                          </div>
                      </div>
                  </div>
              </div>
          </div>

        <!-- View User Modal -->
        <div class="modal" id="viewUserModal">
            <div class="modal-dialog">
                <div class="modal-content">
                    <!-- Modal Header -->
                    <div class="modal-header">
                        <h4 class="modal-title">Employee Detail</h4>
                        <button type="button" class="close modelCloseView" data-dismiss="modal">&times;</button>
                    </div>
                    <!-- Modal body -->
                    <div class="modal-body">
                        <div id="viewUserModalBody">

                        </div>
                    </div>
                    <!-- Modal footer -->
                    <div class="modal-footer">
                        <button type="button" class="btn btn-danger modelCloseView" data-dismiss="modal">Close</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Edit User Modal -->
        <div class="modal" id="editUserModal">
            <div class="modal-dialog">
                <div class="modal-content">
                    <!-- Modal Header -->
                    <div class="modal-header">
                        <h4 class="modal-title">Employee Edit</h4>
                        <button type="button" class="close modelClose" data-dismiss="modal">&times;</button>
                    </div>
                    <!-- Modal body -->
                    <div class="modal-body">
                        <div class="alert alert-danger alert-dismissible fade show" role="alert" style="display: none;">
                            <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                        </div>
                        <div class="alert alert-success alert-dismissible fade show" role="alert" style="display: none;">
                            <strong>Success!</strong>Employee was updated successfully.
                            <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                        </div>
                        <div id="editUserModalBody">

                        </div>
                    </div>
                    <!-- Modal footer -->
                    <div class="modal-footer">
                        <button type="button" class="btn btn-success" id="submitEditUserForm">Update</button>
                        <button type="button" class="btn btn-danger modelClose" data-dismiss="modal">Close</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Delete User Modal -->
        <div class="modal" id="deleteUserModal">
            <div class="modal-dialog">
                <div class="modal-content">
                    <!-- Modal Header -->
                    <div class="modal-header">
                        <h4 class="modal-title">Employee Delete</h4>
                        <button type="button" class="close" data-dismiss="modal">&times;</button>
                    </div>
                    <!-- Modal body -->
                    <div class="modal-body">
                        <h4>Are you sure want to delete this Employee?</h4>
                    </div>
                    <!-- Modal footer -->
                    <div class="modal-footer">
                        <button type="button" class="btn btn-danger" id="SubmitDeleteArticleForm">Yes</button>
                        <button type="button" class="btn btn-default" data-dismiss="modal">No</button>
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
            <footer class="footer">
                Powered by People™ ©2022. All Rights Reserved
            </footer>
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
export default {
  name: 'HelloWorld',
  props: {
      msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>