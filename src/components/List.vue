<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <p class="list-counter">total: {{ totalCardInList }}</p>
      <div class="deletelist" @click="removeList">×</div>
    </div>
    <draggable group="cards"
               :list="cards"
                @end="$emit('change')">
      <card v-for="(item, index) in cards"
            :body="item.body"
            :key="item.id"
            :cardIndex="index"
            :listIndex="listIndex"
      />
      <card-add :listIndex="listIndex" />
    </draggable>
  </div>
</template>

<style scoped>
.list {
  margin-right:15px;
  position: relative;
  display: inline-block;
  flex-direction: column;
  align-items: flex-start;
  width: 290px;
  background-color: #e0e0e0;
  border-radius: 8px;
  padding: 15px;
  border: solid #ddd 1px;
  color: gray;
  vertical-align: top;
}
.listheader {
  display: inline-flex;
  justify-content: space-between;
}
.list-title {
  font-size: 20px;
  font-weight: bold;
  padding: 15px;
}
.list-counter {
  color: rgb(0, 140, 255);
  padding-top: 20px;
}
.deletelist {
  position: absolute;
  top: 1px;
  right: 14px;
  font-size: 28px;
}
.deletelist:hover {
  opacity: 0.8;
  cursor: pointer;
}
</style>
<script>
import CardAdd from './CardAdd'
import Card from './Card'
import draggable from 'vuedraggable'

export default {
  components: {
    draggable,
    CardAdd,
    Card
  },
  props: {
    title: {
      type: String,
      required: true
    },
    cards: {
    type: Array,
    required: true
  },
    listIndex: {
      type: Number,
      required: true
    }
  },
  computed: {
  totalCardInList() {
    return this.cards.length
  }
},
  methods: {
    removeList: function() {
      if(confirm('本当にこのリストを削除しますか？')){
        this.$store.dispatch('removelist', { listIndex: this.listIndex })
      }
    },
  }
}
</script>