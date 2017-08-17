<template>
  <!-- App -->
  <div id="app">
    <!-- Main Views -->
    <f7-views>
      <f7-view id="main-view" navbar-through :dynamic-navbar="true" main>
        <!-- iOS Theme Navbar -->
        <f7-navbar v-if="$theme.ios">
          <f7-nav-center sliding>Connect Four</f7-nav-center>
        </f7-navbar>
        <!-- Pages -->
        <f7-pages>
          <f7-page>
            <!-- Material Theme Navbar -->
            <f7-navbar v-if="$theme.material">
              <f7-nav-left>
                <f7-link icon="icon-bars" open-panel="left"></f7-link>
              </f7-nav-left>
              <f7-nav-center sliding>Connect Four</f7-nav-center>
              <f7-nav-right>
                <f7-link icon="icon-bars" open-panel="right"></f7-link>
              </f7-nav-right>
            </f7-navbar>
            <!-- Page Content -->
            <f7-block-title>Connect Four</f7-block-title>
            <f7-block inner>
              <p>Welcome to our game</p>
            </f7-block>
            <f7-block-title>Go to the game</f7-block-title>
            <f7-list>
              <f7-list-item link="/about/" title="Game"></f7-list-item>
            </f7-list>

          </f7-page>
        </f7-pages>
      </f7-view>
    </f7-views>


  </div>
</template>

<script>
export default {}
</script>
