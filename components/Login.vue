<template>
  <div>
    <img style="width: 100%" class="mb-3" src="~/assets/smart_draft_logo_2.png" alt="Home" />
    <b-form @submit="onSubmit" v-if="show">
      <b-form-group id="input-group-1" label="Username:" label-for="input-1">
        <b-form-input
          id="input-username"
          v-model="form.username"
          type="text"
          placeholder="Enter username"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input id="input-2" v-model="form.name" placeholder="Enter name"></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4">
        <b-form-group label="Lawyer type">
          <b-form-radio
            v-model="form.selected"
            name="some-radios"
            value="senior"
          >Login as Senior Lawyer</b-form-radio>
          <b-form-radio
            v-model="form.selected"
            name="some-radios"
            value="junior"
          >Login as Junior Lawyer</b-form-radio>
        </b-form-group>
      </b-form-group>

      <b-button type="submit" variant="primary">Login</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        username: "",
        selected: "junior"
      },
      show: true
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      if (this.form.selected == "junior") {
        this.$router.push("/junior_open_case_files");
      }
      //this.$router.push("/?"+JSON.stringify(this.form));
    }
  }
};
</script>