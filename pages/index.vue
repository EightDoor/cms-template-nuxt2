<template>
  <div>
    <Tutorial />
    <div>ip地址: {{ ip }}</div>
    <div>
      vuex {{ counter }}
      <button @click="add">添加</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  layout: 'base',

  async asyncData({ $axios }) {
    const data = await $axios.get('http://icanhazip.com')
    console.log(data.data, 'data')
    return { ip: data.data }
  },
  computed: {
    counter() {
      return this.$store.state.counter
    },
  },
  methods: {
    add() {
      this.$store.commit('increment', this.counter + 1)
    },
  },
}
</script>
<style lang="less"></style>
