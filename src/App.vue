<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <div id="wrapper">
      <nav class="navbar navbar-fixed-top">
        <div class="container-fluid">
          <div class="navbar-btn">
            <button type="button" class="btn-toggle-offcanvas">
              <i class="lnr lnr-menu fa fa-bars"></i>
            </button>
          </div>
          <div class="navbar-brand">
            <a href="javascript:void(0);"
              ><img
                src="@/assets/logo.svg"
                alt="Lucid Logo"
                class="img-responsive logo"
            /></a>
          </div>
        </div>
      </nav>

      <div id="left-sidebar" class="sidebar">
        <div class="sidebar-scroll">
          <div class="user-account">
            <img
              src="@/assets/user.png"
              class="rounded-circle user-photo"
              alt="User Profile Picture"
            />
            <div class="dropdown">
              <span>Welcome,</span>
              <a
                href="javascript:void(0);"
                class="dropdown-toggle user-name"
                data-toggle="dropdown"
                ><strong>Alizee Thomas</strong></a
              >
              <ul class="dropdown-menu dropdown-menu-right account">
                <li>
                  <a href="javascript:void(0);"
                    ><i class="icon-user"></i>My Profile</a
                  >
                </li>
                <li>
                  <a href="javascript:void(0);"
                    ><i class="icon-envelope-open"></i>Messages</a
                  >
                </li>
                <li>
                  <a href="javascript:void(0);"
                    ><i class="icon-settings"></i>Settings</a
                  >
                </li>
                <li class="divider"></li>
                <li>
                  <a href="javascript:void(0);"
                    ><i class="icon-power"></i>Logout</a
                  >
                </li>
              </ul>
            </div>
            <hr />
            <ul class="row list-unstyled">
              <li class="col-4">
                <small>Sales</small>
                <h6>456</h6>
              </li>
              <li class="col-4">
                <small>Order</small>
                <h6>1350</h6>
              </li>
              <li class="col-4">
                <small>Revenue</small>
                <h6>$2.13B</h6>
              </li>
            </ul>
          </div>
          <nav id="left-sidebar-nav" class="sidebar-nav">
            <ul id="main-menu" class="metismenu">
              <li>
                <router-link to="/"
                  ><i class="icon-user"></i> <span>Add User</span></router-link
                >
              </li>
              <li>
                <a href="javascript:void(0);"
                  ><i class="icon-users"></i> <span>Users</span></a
                >
              </li>
            </ul>
          </nav>
        </div>
      </div>

      <div id="main-content">
        <div class="container-fluid">
          <router-view />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss"></style>
