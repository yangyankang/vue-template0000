<template>
    <div>
      <Header></Header>
      <div class="article_list">
        <ul>
          <li v-for="(i,index) in list" :key="index">
            <time v-text="$util.goodTime(i.create_at)"></time>
            <router-link :to="'/content/' + i.id">
              {{ i.title }}
            </router-link>
          </li>
        </ul>
      </div>
      <Footer></Footer>
    </div>
</template>
<script>
import Header from '../components/header'
import Footer from '../components/footer'
export default{
  data () {
    return {
      list: []
    }
  },
  components: {
    Header,
    Footer
  },
  created () {
    this.$api.get('topics', null, r => {
      console.log(r)
      if (r.success) {
        this.list = r.data
      }
    })
  }
}
</script>
<style>

</style>
