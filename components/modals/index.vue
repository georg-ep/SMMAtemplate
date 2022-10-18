<template>
  <div>
    <Auth :show="modal && modal.type === 'auth' && modal.show" />
  </div>
</template>

<script>
import Auth from "~/components/modals/Auth.vue";
export default {
  name: "Modals",
  components: {
    Auth,
  },
  computed: {
    modal() {
      return this.$store.getters.modal;
    },
  },
};
</script>