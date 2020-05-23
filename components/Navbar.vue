<template>
  <b-navbar variant="light" type="light" class="bg rounded-bottom shadow-sm mb-4" sticky>
    <b-container>
      <b-navbar-brand :to="url">
        <img
          id="logo"
          src="~/assets/smart_draft_logo_2.png"
          class="d-inline-block align-top"
          alt="Home"
        />
      </b-navbar-brand>
      <div>
        <b-dropdown
          size="lg"
          variant="link"
          class="mr-2"
          toggle-class="text-decoration-none"
          no-caret
          right
        >
          <template v-slot:button-content>
            <b-icon-bell size="lg" />
            <b-badge>3</b-badge>
            <span class="sr-only">Notifications</span>
          </template>
          <b-dropdown-item href="#">
            <b-icon-exclamation-triangle class="mr-2" />Work contract about to expire (4 days)
          </b-dropdown-item>
          <b-dropdown-item href="#">
            <b-icon-bell class="mr-2" />Reminder for NDA
          </b-dropdown-item>
          <b-dropdown-item href="#">
            <b-icon-check-all class="mr-2" />Contract signed by oposing party
          </b-dropdown-item>
        </b-dropdown>
        <b-button variant="outline-primary" to="/">Logout</b-button>
      </div>
    </b-container>
  </b-navbar>
</template>

<script>
import {
  BIconBell,
  BIconExclamationTriangle,
  BIconCheckAll
} from "bootstrap-vue";
export default {
  props: {
    url: {
      default: "/",
      type: String
    }
  },
  components: {
    BIconBell,
    BIconExclamationTriangle,
    BIconCheckAll
  }
};
</script>
<style>
#logo {
  width: 200px;
}
</style>
