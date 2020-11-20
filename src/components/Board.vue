<template>
  <div>
    <header>
      my Trello
    </header>
    <main>
      <p class="info-line">All: {{ totalCardCount }} tasks</p>
      <draggable :list="lists"
                  @end="movingList"
                  class="list-index">
        <list v-for="(item, index) in lists"
              :key="item.id"
              :title="item.title"
              :cards="item.cards"
              :listIndex="index"
              @change="movingCard"
        />
        <list-add />
      </draggable>
    </main>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
import ListAdd from './ListAdd.vue'
import List from './List'
import { mapState } from 'vuex'

export default {
  components: {
    draggable,
    ListAdd,
    List,
  },
  computed: {
    ...mapState([
      'lists'
    ]),
      totalCardCount() {
      return this.$store.getters.totalCardCount
    }
  },
  methods: {
    movingCard: function() {
      this.$store.dispatch('updateList', { lists: this.lists })
    },
    movingList: function() {
      this.$store.dispatch('updateList', { lists: this.lists })
    }
  }
}
</script>
<style scoped>
header {
  background: rgb(0, 195, 255);
  color: white;
  font-style: italic;
  font-size: 40px;
  text-align: left;
  padding: 10px 0 0 20px;
}
main {
  padding: 0 20px;
  width: calc(100% - 40px);
  height: 100%;
}
.info-line {
  margin-bottom: 20px;
  font-size: 20px;
  color: white;
}
</style>