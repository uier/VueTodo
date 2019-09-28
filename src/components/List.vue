<template>
  <b-container>
    <b-container class="input">
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
        <b-input-group class="mt-3">
          <b-form-input required ref="getFocus" v-model="text" placeholder="Add a new Todo (shortcut: Enter)"></b-form-input>
          <b-input-group-append>
            <b-button type="reset" variant="danger"><font-awesome-icon icon="eraser" /></b-button>
            <b-button type="submit" variant="primary"><font-awesome-icon icon="plus" /></b-button>
          </b-input-group-append>
        </b-input-group>
      </b-form>
    </b-container>
    <b-container class="list mt-3">
      <b-tabs fill justify>
        <!-- two pages -->
        <b-tab v-for="n in 2" class="data">
          <!-- tab title -->
          <template v-slot:title>
            {{ title[n-1] }} <b-badge variant="primary" v-if="n==1&&items[n-1].length>0">{{ items[n-1].length }}</b-badge>
          </template>
          <!-- todo list -->
          <b-list-group>
            <!-- if empty then print empty -->
            <div v-if="items[n-1].length===0" class="mt-5 text-muted">Empty</div>
            <!-- for_all button -->
            <b-list-group-item v-if="items[n-1].length>0" class="text-right">
              <b-button v-if="n===1" @click="RemoveAll(n-1, 1)" variant="outline-success" class="mr-1">Solve all</b-button>
              <b-button v-else @click="RemoveAll(n-1, 1)" variant="outline-success" class="mr-1">Unsolve all</b-button>
              <b-button @click="RemoveAll(n-1, 2)" variant="outline-danger">Remove all</b-button>
            </b-list-group-item>
            <!-- todo info -->
            <b-list-group-item v-for="(item, index) in items[n-1]" class="d-flex space-between">
              <b-col cols="8" class="text-left p-0">
                {{ item.data }}<br><b-badge variant="info">{{ item.timestamp }}</b-badge>
              </b-col>
              <!-- solve & remove button -->
              <b-col cols="4" class="text-right p-0 ">
                <b-button v-if="n===1" @click="Remove(index, n-1, 1)" variant="outline-success" class="mr-1"><font-awesome-icon icon="check" /></b-button>
                <b-button v-else @click="Remove(index, n-1, 1)" variant="outline-success" class="mr-1"><font-awesome-icon icon="reply" /></b-button>
                <b-button @click="Remove(index, n-1, 2)" variant="outline-danger"><font-awesome-icon icon="trash-alt" /></b-button>
              </b-col>
            </b-list-group-item>
          </b-list-group>
        </b-tab>
      </b-tabs>
    </b-container>
  </b-container>
</template>

<script>
// import swal from 'https://unpkg.com/sweetalert/dist/sweetalert.min.js'

export default {
  name: 'List',
  data () {
    return {
      text: '',
      show: true,
      title: ['Todo', 'Completed'],
      items: [
        [], [], []
      ]
    }
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      this.items[0].push({data: this.text, timestamp: new Date().toJSON().slice(0,10).replace(/-/g,'/')})
      this.text = ''
      this.$refs.getFocus.focus()
      // this.onShow()
    },
    onReset(evt) {
      evt.preventDefault();
      this.text = ''
      this.$refs.getFocus.focus()
      // this.onShow()
    },
    Remove(idx, begin, target) {
      if ( target === 1 ) {
        this.items[begin^1].push(this.items[begin][idx])
      }
      this.items[begin].splice(idx, 1)
      this.onShow()
    },
    RemoveAll(begin, target) {
      if ( target === 1 ) {
        this.items[begin].forEach((obj) => {
          this.items[begin^1].push(obj)
        })
      }
      this.items[begin] = []
      this.onShow()
    },
    onShow() {
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.input {
  max-height: 20vh;
  width: 30vw;
}

.list {
  height: 60vh;
  width: 40vw;
}

.data {
  max-height: 50vh;
  overflow-y: scroll;
}
</style>
