<template>
	<div>
		<Header></Header>
    <List></List>
    <br>
    <Dialog>
      <b slot="btnText">Tips</b>
      <h2 slot="header">Tips for VueTodo</h2>
      <p slot="content">You can Add any Todo from the text input.</p>
      <p slot="content">cnt: {{ cnt }} (click count to increment)</p>
      <b-button slot="otherAction" size="sm" variant="danger" @click="increment">
        Count
      </b-button>
      </b>
    </Dialog>
	</div>
</template>

<script>
import Header from '@/components/Header.vue'
import List from '@/components/List.vue'
import Dialog from '@/components/Dialog.vue'

export default {

  name: 'Main',
  components: {
    Header, List, Dialog
  },
  data () {
    return {
      cnt: 0,
    }
  },
  methods: {
    increment() {
      this.cnt++;
    },
  },
}
</script>

<style lang="css" scoped>
</style>