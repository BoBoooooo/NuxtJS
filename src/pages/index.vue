<template>
  <div class="container">
    <h1>{{ info.t }}</h1>
  </div>
</template>

<script lang="ts">
export default {
  async asyncData({ $axios, ctx }) {
    try {
      const response = await $axios({
        method: 'get',
        url: 'http://api.m.taobao.com/rest/api3.do?api=mtop.common.getTimestamp'
      })
      // throw new Error()
      return { info: response.data.data }
    } catch {
      ctx.error({ statusCode: 500, message: '服务器开小差了~' })
    }
  },
  data() {
    return {
      value: ''
    }
  },
  mounted() {
    // this.$alert(this.info.t)
  },
  head() {
    return {
      title: '百度--搜了个啥',
      meta: [{ hid: 'index', name: 'index', content: 'index page' }]
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
