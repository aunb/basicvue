<template>
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
                    <router-link  class="sidebar-link waves-effect waves-dark sidebar-link" to="/about"
                        aria-expanded="false">
                    <span class="hide-menu">User list </span></router-link >
                </li>   
                    <li class="sidebar-item">
                    <router-link  class="sidebar-link waves-effect waves-dark sidebar-link" to="/Contact-us"
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
</template>
