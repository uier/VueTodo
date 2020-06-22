<template>
	<div>
		<Header></Header>
    <List></List>
    <br>
    <Dialog>
      <b slot="btnText">Info</b>
      <h2 slot="header">Information</h2>
      <p slot="content">
        Hi! This is a side project for practicing Vue.js.
        <br>
        The data is stored with Local Storage, and will not be cleared after you closing the browser.
        <br>
        <br>
        Developer: TzuWei YU (Uier)
      </p>
      <div slot="otherAction"/>
    </Dialog>
    <br>
    <!-- Place this tag where you want the button to render. -->
    <a class="github-button" href="https://github.com/Uier/VueTodo" data-size="large" data-icon="octicon-star" data-show-count="true" aria-label="Star Uier/VueTodo on GitHub">Star</a>
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
}
</script>

<style lang="css" scoped>
</style>