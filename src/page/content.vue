<template>
    <div>
      <myHead></myHead>
      <h2 v-text="data.title"></h2>
      <p>作者:{{data.author.loginname}} &nbsp;&nbsp;发表于：{{$utils.goodTime(data.create_at)}}</p>
      <hr>
      <article v-html="data.content"></article>
      <h3>网友回复：</h3>
      <ul>
        <li v-for="(i, index) in data.replies" :key="index" >
          <p>评论者：{{i.author.loginname}}&nbsp;&nbsp;评论于：{{$utils.goodTime(i.create_at)}}</p>
          <article v-html="i.content"></article>
        </li>
      </ul>
      <myFooter></myFooter>
    </div>
</template>
<script>
import myHead from '../components/header'
import myFooter from '../components/footer'

export default{
  data () {
    return {
      msg: 'hello vue',
      id: this.$route.params.id,
      data: {}
    }
  },
  components: {
    myHead,
    myFooter
  },
  methods: {
    getData () {
      this.$api.get('topic/' + this.id, null, r => {
        this.data = r.data
      })
    }
  },
  created () {
    this.getData()
  }
}
</script>
<style>

</style>
