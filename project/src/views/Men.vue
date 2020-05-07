<template>
  <body>

    <div class="new_arrivals_sector">
      <div class="new_arrivals">new arrivals</div>
      <ul class="bread_crumbs">
        <li><a class="bread_home bread_link" href="/">home/</a></li>
        <li><a class="bread_men bread_link" href="/men">men/</a></li>
        <li><a class="bread_new bread_link" href="#">new arrivals</a></li>
      </ul>
    </div>
    <div class="men_product center">
      <div class="left_bar">
        <details open>
          <summary class="drop_down_summary">Category</summary>
          <ul class="drop_down_ul">
            <li><a href="">Accessorie</a></li>
            <li><a href="">Bag</a></li>
            <li><a href="">Deni</a></li>
            <li><a href="">Hoodies & Sweatshirt</a></li>
            <li><a href="">Jackets & Coat</a></li>
            <li><a href="">Pants Polo</a></li>
            <li><a href="">Shirt</a></li>
            <li><a href="">Shoe</a></li>
            <li><a href="">Short</a></li>
            <li><a href="">Sweaters & Knit</a></li>
            <li><a href="">T-Shirts</a></li>
            <li><a href="">Tanks</a></li>
          </ul>
        </details>
        <details>
          <summary class="drop_down_summary">brand</summary>
          <ul class="drop_down_ul"></ul>
        </details>
        <details>
          <summary class="drop_down_summary">designer</summary>
          <ul class="drop_down_ul"></ul>
        </details>
      </div>
      <div class="right_product">
        <div class="trending_now_right">
          <h3 class="trending_h">Trending now</h3>
          <ul class="right_ul">
            <li class="span_right">
              <a class="link_right" href="">Bohemian</a>
            </li>
            <li class="span_right"><a class="link_right" href="">Floral</a></li>
            <li class="span_right"><a class="link_right" href="">Lace</a></li>
            <li class="span_right"><a class="link_right" href="">Floral</a></li>
            <li class="span_right"><a class="link_right" href="">Lace</a></li>
            <li class="span_right">
              <a class="link_right" href="">Bohemian</a>
            </li>
          </ul>
        </div>
        <div class="size_right">
          <h3>size</h3>

          <ul class="size_ul">
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="XXS" class="size_input" /><label
                for="XXS"
                class="label_size size_xxs"
                >XXS</label
              >
            </li>
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="XS" class="size_input" /><label
                for="XS"
                class="label_size size_xs"
                >XS</label
              >
            </li>
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="S" class="size_input" /><label
                for="S"
                class="label_size size_s"
                >S</label
              >
            </li>
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="M" class="size_input" /><label
                for="M"
                class="label_size size_m"
                >M</label
              >
            </li>
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="L" class="size_input" /><label
                for="L"
                class="label_size size_l"
                >L</label
              >
            </li>
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="XL" class="size_input" /><label
                for="XL"
                class="label_size size_xl"
                >XL</label
              >
            </li>
            <li class="size_boxes">
              <input @click="size" type="checkbox" id="XXL" class="size_input" /><label
                for="XXL"
                class="label_size size_xxl"
                >XXL</label
              >
            </li>
          </ul>
        </div>
        <div class="price_right">
          <h3>price</h3>
          <div id = "doubleRange">
<div class="container">
    <input id="range2" @input="change2" type="range" min="0" step="1" :max="valConst" :value="val2" class="range">
    <input id="range" @input="change" class = "range" :style="{background: '-webkit-linear-gradient(left ,#fff 0%, #fff '+(val*100)/valConst+'%, #f16d7f '+(val*100)/valConst+'%,#f16d7f '+(val2*100)/valConst+'%,#fff '+(val2*100)/valConst+'%, #fff 100%)'}" type="range" min="0" step="1" :max="valConst" :value="val">
   
          <label for="range">
            <p class="range_from">{{val}} &#8381;</p>
            <p class="range_to">{{val2}} &#8381;</p>
          </label>
</div>

          </div>
        </div>
        <div class="sort">
          <div  class="first">
            <div @click.prevent="dropDownShow" class="sort_hover sort_sort_by"><a href="#">Sort By</a></div>
            <div @click="dropDownShow" class="sort_hover sort_name">{{sortBy}}</div>
            <ul @click="changeSortBy" @mouseleave="dropDownHide"  class="sort-ul" v-show="check">
                <button class="sort-li"><li>Name</li></button>
                <button class="sort-li"><li>Price</li></button>
                <button class="sort-li"><li>Category</li></button>
            </ul>
          </div>
          <div class="second">
            <div @click.prevent="dropDownAtPageShow" class="sort_hover sort_show"><a href="#">Show</a></div>
            <div @click.prevent="dropDownAtPageShow" class="sort_hover sort_figure"><a href="#">{{atPage}}</a></div>
              <ul @click="changeAtPage" @mouseleave="dropDownAtPageHide"  class="sort-ulAtPage" v-show="checkAtPage">
                <button class="sort-li"><li>6</li></button>
                <button class="sort-li"><li>9</li></button>
                <button class="sort-li"><li>12</li></button>
            </ul>

          </div>
        </div>
        <div class="product-box center">
          <prodMen :arrayMen="arrayMen"/>
        </div>
        <div class="middle_men">

          <div class="pagination_men">
            <ul class="pagination_ul">
              <li class="pagination_li">
                <button :class="{disabled: currentPage === 0}" :disabled="currentPage === 0" @click.prevent="toLeft" href="#" class="pagination_link paginationButton"
                  ><i class="fas fa-angle-left"></i
                ></button>
              </li>
              <li @click.prevent="changePage" v-for="page of arrayPages" :key="page" class="pagination_li">
                <button :disabled="arrayPages.length === 1" href="#" :class="{active_men: currentPage === page}" class="pagination_link paginationButton">{{page + 1}}</button>
              </li>
              <li class="pagination_li">
                <button :class="{disabled: currentPage === arrayPages.length - 1}" :disabled="currentPage === arrayPages.length - 1" @click.prevent="toRight" href="#" class="pagination_link paginationButton"
                  ><i class="fas fa-angle-right"></i
                ></button>
              </li>
            </ul>
          </div>


          <div class="men_view_all">
            <a class="men_view_all_link" href="#">View All</a>
          </div>
        </div>
      </div>
    </div>

    <section class="right_block_men">
      <div class="offer_content_men">
        <img
          class="offer_picture"
          src="../assets/img/offer/truck.png"
          alt="truck"
        />
        <article class="text">
          <p class="free_Delivery">Free Delivery</p>
          <p class="world_wide">
            Worldwide delivery on all. Authorit tively morph next-generation
            innovation with extensive models
          </p>
        </article>
      </div>
      <article class="offer_content">
        <img
          class="offer_picture"
          src="../assets/img/offer/percent.png"
          alt="%"
        />
        <div class="text">
          <p class="free_Delivery">Sales & discounts</p>
          <p class="world_wide">
            Worldwide delivery on all. Authorit tively morph next-generation
            innovation with extensive models
          </p>
        </div>
      </article>

      <article class="offer_content">
        <img
          class="offer_picture"
          src="../assets/img/offer/crown.png"
          width="109px"
          alt="%"
        />
        <div class="text">
          <p class="free_Delivery">Quality assurance</p>
          <p class="world_wide">
            Worldwide delivery on all. Authorit tively morph next-generation
            innovation with extensive models
          </p>
        </div>
      </article>
    </section>
  </body>
</template>

<script>
import prodMen from '@/components/productsMen.vue'
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'men',
  data () {
    return {
        array: [{price: 0}, {price:1}],
        val: null,
        val2: null,
        valConst: null,
        arrayMen: [],
        sortBy: 'Name',
        check: false,
        sortByProperty: '',
        sortBySize: [], 
        tempArrayMen: [],
        atPage: 6,
        pages: null,
        currentPage: 0,
        arrayPages: [],
        paginationArray: [],
        checkAtPage: false,

    }
  },
  components: { prodMen },
  methods: {
dropDownAtPageShow(){
 this.checkAtPage = true
},
dropDownAtPageHide(){
 this.checkAtPage = false
},
changeAtPage(){
this.atPage = event.target.innerText
this.filterArrMen()
},
toLeft(){
  this.currentPage--
  this.arrayMen = this.paginationArray
  this.pagination()
},
toRight(){
  this.currentPage++
  this.arrayMen = this.paginationArray
  this.pagination()
},

    size(){
      if (!event.toElement.checked){
       let index = this.sortBySize.findIndex(el => el === event.target.id)
        this.sortBySize.splice(index, 1)
        this.filterArrMen()
      } else {
        this.sortBySize.push(event.target.id)
        this.filterArrMen()
      }
    },
      dropDownShow(){
          this.check = true
      },
    dropDownHide(){
          this.check = false
      },
    ...mapActions(['fetchProdData']),
    change () {
        this.val = +event.target.value
        if ((+this.val) > +this.val2){
            this.val2 = +this.val
        
        }
        this.filterArrMen()


    },
        change2 () {
        this.val2 = +event.target.value
        if ((+this.val2) < (+this.val)){
            this.val = +this.val2
        }
        this.filterArrMen()

    },
    sort(){
        this.array.sort((a,b) => {
            if (a.price > b.price) {
                return 1
            }
            if (a.price < b.price) {
                return -1
            }
            return 0
        })
    },
    changeSortBy(){
        this.sortBy = event.target.innerText
        this.filterArrMen()
    },
    valsAssign(){
        this.val = this.array[0].price
        this.val2 = this.array[this.array.length-1].price
        this.valConst = this.array[this.array.length-1].price

    },
    filterArrMen(){
        this.arrayMen = this.getProdData.filter(el => el.sex === 'men')
        this.arrayMen = this.arrayMen.filter(el => el.price >= this.val && el.price <= this.val2)
                switch (this.sortBy){
                case 'Name':  this.sortByProperty = 'product_name'
                break
                case 'Price': this.sortByProperty = 'price'
                break
                case 'Category': this.sortByProperty = 'category'
                break
            }
        this.arrayMen.sort((a,b) => {

            if (a[this.sortByProperty] > b[this.sortByProperty]) {
                return 1
            }
            if (a[this.sortByProperty] < b[this.sortByProperty]) {
                return -1
            }
            return 0
        })
        this.getArrayBySize()
        // this.arrayMen = this.paginationArray
        this.pagination()
    },
    getArrayBySize(){
      this.tempArrayMen=[]
      if (this.sortBySize.length){
        this.arrayMen.forEach(el => {
          this.sortBySize.forEach(size => {
            if (el.size.includes(size) && !this.tempArrayMen.includes(el)){
              this.tempArrayMen.push(el)
            }
          })
          
        })
      this.arrayMen = this.tempArrayMen
      }

    },

    getPagesArray(){
        this.arrayPages = []
        this.pages = Math.ceil(this.arrayMen.length / this.atPage)
        for (let i = 0; i < this.pages; i++){
          if(!this.arrayPages.includes(i)) {
            this.arrayPages.push(i)
          }
        }
    },
    pagination(){
      
       if (this.arrayMen.length < this.atPage) { 
         this.getPagesArray()
         this.currentPage = 0
         this.arrayMen = this.arrayMen
       } else {
         this.paginationArray = this.arrayMen
        this.getPagesArray()
       this.arrayMen = this.paginationArray.slice(this.currentPage * this.atPage, this.currentPage * this.atPage + this.atPage)
      }
    },

    changePage(){
      this.currentPage = +event.target.innerText-1
      this.arrayMen = this.paginationArray
      this.pagination()
    }

  },
  computed: {
    ...mapGetters(['getProdData', 'getArrMen', 'getArrWomen'])
  },
  mounted () {

      window.addEventListener('load', () => {
      this.fetchProdData()  
      this.array = this.getProdData
          this.sort()
          this.valsAssign()
          this.filterArrMen()
          // this.pagination()
      })
    this.fetchProdData()
    if (this.getProdData.length){
      this.array = this.getProdData
          this.sort()
          this.valsAssign()
          this.filterArrMen()
          // this.pagination()
      }

  }
}
</script>

<style scoped>
.container{
  position: relative;
  pointer-events: none;
}

input[type="range"]::-webkit-slider-thumb {
  pointer-events: all;
}
input[type="range"]::-moz-range-thumb {
  pointer-events: all;
}
input[type="range"]::-ms-thumb {
  pointer-events: all;

}

#range2{
    margin-bottom:-1em;
    
}

.range{
    -webkit-appearance: none;
    border-radius:20px;
    width:230px;
    outline : none;
    border:1px solid #D4D4D4;
    height: 1em;
    display: block;
    margin: 0;
}

.dropDown{
    display: none;
}
.first, .second{
    position: relative;
}
.sort-ul{
    display: flex;
    flex-direction: column;
    position: absolute;
    left: 79px;
    top: 26px;
    list-style-type: none;
    width: 57px;
}

.sort-ulAtPage{
    display: flex;
    flex-direction: column;
    position: absolute;
    left: 59px;
    top: 26px;
    list-style-type: none;
    width: 57px;
}
.sort-li{
    height: 20px;
    cursor: pointer;
    border-style: none;
    outline: none;
}

.sort-li:hover{
    background-color: #f16d7f;
    color: white;
}
.sort_name{
    font-size: 14px;
    color: #6f6e6e;
    padding: 3px;
}
.sort_name:hover{
    background-color: #f16d7f;
    color: white;
}
.paginationButton {
    border: none;
    cursor: pointer;
    outline: none;
}
.disabled:hover {
  color: silver;
}
</style>