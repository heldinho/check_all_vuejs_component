<template>
  <div>
    <CheckAll :selectAll="selectAll" @update="allSelect" />
    <p v-for="item in items" :key="item.id" style="margin-left: 20px;">
      <Check :item="item" @input="select" :selected="selected" />
    </p>
  </div>
</template>

<script>
import CheckAll from './components/CheckAll'
import Check from './components/Check'

export default {
  name: 'app',
  components: {
    CheckAll,
    Check
  },
  data() {
    return {
      selected: [],
      items: [
        { id: 1, label: 'PHP' },
        { id: 2, label: 'Node' },
        { id: 3, label: 'React' },
        { id: 4, label: 'Vue' },
        { id: 5, label: 'Go' }
      ]
    }
  },
  methods: {
    allSelect: function(val) {
      this.selectAll = val
    },
    select: function(e) {
      if (e.target.checked) {
        this.selected.push(Number(e.target.id))
      } else {
        var index = this.selected.indexOf(Number(e.target.id))
        if (index > -1) {
          this.selected.splice(index, 1)
        }
      }
    },
  },
  computed: {
    selectAll: {
      get: function() {
        return this.items ? this.selected.length == this.items.length : false
      },
      set: function(value) {
        var selected = []
        if (value) {
          this.items.forEach(function(e) {
            selected.push(e.id)
          })
        }
        this.selected = selected;
      }
    }
  }
}
</script>

<style></style>
