<template>
  <RegiestForm 
  v-bind:profile="profile" />
</template>
<script>
import RegiestForm from "./components/RegiestForm.vue";
export default {
  name: "App",
  components: {
    RegiestForm,
  },
  data() {
    return {
      msg: "",
      profile : {} 
    };
  },
  beforeCreate() {
    // eslint-disable-next-line no-unused-vars
    window.liff
      .init({
        liffId: "<your liffId>", // Use own liffId
      })
      .then(() => {
        // Start to use liff's api
        this.getProfile();
      })
  },
  methods: {
    getProfile: function () {
      window.liff
        .getProfile()
        .then((profile) => {
          this.profile = profile;
        })
    },
  },
};
</script>
<style>
</style>