<template>
  <b-modal v-model="modalShow">
    <p class="my-4">Hello from modal!</p>
  </b-modal>
</template>

<script>
export default {
  name: "whatsappDisconnectModal",
  props: {
    show: {
      type: Boolean,
      default: true,
      required: true,
    },
    params: {
      type: Object,
    },
  },
  computed: {
    modalShow() {
      return this.show;
    },
  },
};
</script>