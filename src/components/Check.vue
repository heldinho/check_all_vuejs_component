<template>
  <div>
    <input type="checkbox" :value="item.id" :id="item.id" @change="input" v-model="selected" />
    <label :for="item.id">{{ item.label }}</label>
  </div>
</template>

<script>
  export default {
    name: 'checkall',
    props: ['item', 'selected'],
    methods: {
      input: function(e) {
        this.$emit('input', e)
      }
    },
    computed: {
      check: {
        get: function () { return this.selected },
        set: function (value) { this.$emit('find', value) },
      }
    }
  }
</script>
