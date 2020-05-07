<template>
  <div>
    <div class="new_arrivals_sector">
      <div class="new_arrivals">new arrivals</div>
      <ul class="bread_crumbs">
        <li>
          <a class="bread_home bread_link" href="/">home/</a>
        </li>
        <li>
          <a class="bread_men bread_link" href="men">men/</a>
        </li>
        <li>
          <a class="bread_new bread_link" href="#">new arrivals</a>
        </li>
      </ul>
    </div>
    <div class="single_page">
      <carousel :prod="$store.state.singleProd" @slidetoright="slideToRight" @slidetoleft="slideToLeft"/>
      <!-- <div class="single_page_first">
        <a class="single_page_arrows" href="#">
          <i class="fas fa-angle-left"></i>
        </a> -->
        <!-- <img alt="women" src="../img/single_page.png"> -->
        <!-- <img id="size" alt="women" :src="'../'+getSingleProd.img" />
        <a class="single_page_arrows" href="#">
          <i @click.prevent="change" class="fas fa-angle-right"></i>
        </a>
      </div> -->
      <div class="single_page_second">
        <h3 class="single_page_second_women">{{getSingleProd.sex}} collection</h3>
        <div class="single_page_second_pagination">
          <a class="single_page_second_pagination_links" href="#"></a>
          <a class="single_page_second_pagination_links single_page_active" href="#"></a>
          <a class="single_page_second_pagination_links" href="#"></a>
        </div>
        <p class="single_page_second_moschino">Moschino Cheap And Chic</p>
        <p class="single_page_second_text">
          Compellingly actualize fully researched processes before proactive
          outsourcing. Progressively syndicate collaborative architectures before cutting-edge services. Completely
          visualize parallel core competencies rather than exceptional portals.
        </p>
        <div class="single_page_second_cotton">
          <span class="single_page_second_cotton_material">material:</span>
          <span class="single_page_second_cotton_cotton" style="margin-right: 44px">cotton</span>
          <span class="single_page_second_cotton_designer">designer:</span>
          <span class="single_page_second_cotton_bin">BINBURHAN</span>
          <p class="single_page_second_dollar">{{getSingleProd.price}} &#8381;</p>
        </div>

        <div class="single_page_second_block">
          <div class="single_page_second_in">
            <p>choose color</p>
            <select class="single_page_second_choose name">
              <option value="red">red</option>
              <option value="blue">blue</option>
              <option value="yellow">yellow</option>
            </select>
          </div>
          <div class="single_page_second_in" style="margin: 0 53px">
            <p>choose size</p>
            <select class="single_page_second_choose name">
              <option value="red">XXS</option>
              <option value="blue">XS</option>
              <option value="yellow">S</option>
              <option value="red">L</option>
              <option value="blue">XL</option>
              <option value="yellow">XXL</option>
            </select>
          </div>
          <div class="single_page_second_in">
            <p>quantity</p>
            <input class="single_page_second_choose_input" id="quantity" type="number" value="2" />
          </div>
        </div>
        <a class="single_page_button" href="#">Add to Cart</a>
      </div>
      <div class="single_page_third_h">you may like also</div>
      <div class="center single_page_third_like">
        <likealso v-for="item of getLikeAlso" :key="item.id_product" :item="item" @add="add" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
import likealso from "@/components/likeAlso.vue";
import carousel from "@/components/carousel.vue";
export default {
  data() {
    return {
      prodId: "",
      prod: {},
      prods: [],
      array: [],
      prodArray: [],
      prodIndex: "",
      newProd: '',
      index: null
    };
  },
  methods: {

slideToRight() {

  this.$store.state.singleProdNumb++
  this.index = this.$store.state.prodData.findIndex(el => el.id_product === +this.$store.state.singleProdNumb)
  this.$store.state.singleProd = this.$store.state.prodData[this.index]


},
slideToLeft() {

  this.$store.state.singleProdNumb--
  this.index = this.$store.state.prodData.findIndex(el => el.id_product === +this.$store.state.singleProdNumb)
  this.$store.state.singleProd = this.$store.state.prodData[this.index]
  console.log(1)
},

    change() {
      this.$store.state.singleProdNumb++
      this.getSingleProd
      // console.log(this.getProdData[this.getProdData.findIndex(el => el.id_product === prod.id_product)])
      // console.log(this.getProdData.findIndex(el => el.id_product === prod.id_product))
      // this.prodArray = this.getProdData
      // this.prodIndex = this.getProdData.findIndex(
      //   el => el.id_product === prod.id_product
      // );
      // if (this.prodIndex === this.prodArray.length) {
      //   this.prodIndex = 0;
      // } else {
      //   this.prodIndex++;
      // }
      // this.newProd === this.prodArray[this.prodIndex];
    },

    ...mapActions(["fetchProdData"]),
    add(item) {
      console.log(item);
      let find = this.$store.state.cartData.contents.find(
        el => el.id_product === item.id_product
      );
      if (find) {
        this.$store.dispatch("putJson", {
          prod: item,
          url: `http://localhost:3030/api/cart/${find.id_product}`
        });
        find.quantity++;
      } else {
        let prod2 = Object.assign({ quantity: 1 }, item);
        this.$store.dispatch("postJson", {
          prod: prod2,
          url: `http://localhost:3030/api/cart`
        });
        this.$store.state.cartData.contents.push(prod2);
      }
    
    }
  },
  computed: {
    ...mapGetters(["getProdData", "getArrMen", "getArrWomen", "getSingleProd", "getLikeAlso"])
  },
  mounted() {
    this.fetchProdData();
    this.$store.state.singleProdNumb = this.$route.params.id;
  },
  components: {
    likealso,
    carousel
  }
};
</script>
