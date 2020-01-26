<template>
  <div>
    <b-button v-b-modal.modal-1>
      <slot name="btnText">Custom Text</slot>
    </b-button>
    <b-modal id="modal-1">
      <template v-slot:modal-header>
        <slot name="header">
          <h5>Modal Header</h5>
        </slot>
      </template>

      <template v-slot:default="{ close }">
        <slot name="content">
          <p>Custom Modal Body with button</p>
          <b-button @click="close()">Close Modal</b-button>
        </slot>
      </template>

      <template v-slot:modal-footer="{ ok, cancel }">
        <slot name="footer">
          <b>Custom Footer</b>
        </slot>
        <b-button size="sm" variant="success" @click="ok()">
          OK
        </b-button>
        <slot name="otherAction">
          <b-button size="sm" variant="danger" @click="cancel()">
            Cancel
          </b-button>
        </slot>
      </template>
    </b-modal>
  </div>
</template>

<script>
export default {

  name: 'Dialog',

  data () {
    return {
      dialog: false,
    }
  },

  methods: {
  }
}
</script>

<style lang="css" scoped>
</style>