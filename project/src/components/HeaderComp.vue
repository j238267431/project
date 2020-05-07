<template>
<header class="header center">
<div class="header__left">
<a class="logo" href="/">
   <img class="logo__img" src="../assets/img/logo.png" alt="logo">
      <span class="text_shadow">BRAN<div style="position: absolute" class="D bounce-in-bck">D</div>
   </span></a>
   <!-- <search :arrMen="arrMen" :arrWomen="arrWomen" ref="search"/> -->
   <search :featured="featuredArray" :arrMen="categoryArrayMen" :arrWomen="categoryArrayWomen" ref="search"/>
</div>
   <cart ref="cart"/>

</header>

</template>

<script>
import search from '@/components/search.vue';
import cart from '@/components/cart.vue';
import { mapActions, mapGetters } from 'vuex';
import test from '@/components/test.vue'

export default {
  name: 'Header',
  data() {
    return {
      featuredArray: [],
      arrayMen: [],
      categoryArrayMen: [],
      categoryArrayWomen: [],
    };
  },
  components: { search, cart, test },
  methods: {
    ...mapActions(['fetchProdData']),
    filterFeatured(){
      this.featuredArray = this.getProdData.filter(el => el.featured)
      this.$store.state.filtered = this.featuredArray
      console.log(this.$store.state.filtered)

    },
    getArrayMen(){
      this.arrayMen = this.getProdData.filter(el => el.sex === 'men')
      this.arrayMen.forEach(el => {
        if (!this.categoryArrayMen.includes(el.category)){
          this.categoryArrayMen.push(el.category)
        }
      })
      this.$store.state.arrMen = this.categoryArrayMen
    },
    getArrayWomen(){
      this.arrayWomen = this.getProdData.filter(el => el.sex === 'women')
      this.arrayWomen.forEach(el => {
        if (!this.categoryArrayWomen.includes(el.category)){
          this.categoryArrayWomen.push(el.category)
        }
      })
      this.$store.state.arrWomen = this.categoryArrayWomen
    }

  },
  computed: {
    ...mapGetters(['getProdData', 'getArrMen', 'getArrWomen']),
  },
  mounted() {
    this.fetchProdData();
          window.addEventListener('load', () => {
      this.fetchProdData()  
      this.array = this.getProdData
          this.filterFeatured()
          this.getArrayMen()
          this.getArrayWomen()
      })
    this.fetchProdData()
    if (this.getProdData.length){
      this.array = this.getProdData
          this.filterFeatured()
          this.getArrayMen()
          this.getArrayWomen()
      }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
// h3 {
//   margin: 40px 0 0;
// }
// ul {
//   list-style-type: none;
//   padding: 0;
// }
// li {
//   display: inline-block;
//   margin: 0 10px;
// }
// a {
//   color: #42b983;
// }
</style>
