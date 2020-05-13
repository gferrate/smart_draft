<template>
  <b-navbar variant="light" type="light" class="bg rounded-bottom shadow-sm mb-4" sticky>
    <b-container>
      <b-navbar-brand to="/">
        <img
          id="logo"
          src="~/assets/smart_draft_logo_2.png"
          class="d-inline-block align-top"
          alt="Home"
        />
      </b-navbar-brand>
      <b-button variant="outline-primary" to="/">Logout</b-button>
    </b-container>
  </b-navbar>
</template>

<script>
</script>

<style>
#logo {
  width: 200px;
}
.bg {
  /*background-color: #f3f2e2 !important;*/
}
</style>
