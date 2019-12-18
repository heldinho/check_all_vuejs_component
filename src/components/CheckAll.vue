<template>
  <div>
    <input type="checkbox" id="all" v-model="select" />
    <label for="all">Select All</label>
  </div>
</template>

<script>
  export default {
    name: 'CheckAll',
    props: ['selectAll'],
    computed: {
      select: {
        get: function () { return this.selectAll },
        set: function (value) { this.$emit('update', value) },
      }
    }
  }
</script>
