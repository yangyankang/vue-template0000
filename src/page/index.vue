<template>
    <div>
      <header-comp></header-comp>
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
      <footer-comp></footer-comp>
    </div>
</template>
<script>
import HeaderComp from '../components/head'
import FooterComp from '../components/foot'
export default{
  data () {
    return {
      list: []
    }
  },
  components: {
    HeaderComp,
    FooterComp
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
