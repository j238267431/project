<template>
         <div class="single_page_first">
        <button :disabled="$store.state.prodData.indexOf(prod)===0" @click.prevent="$emit('slidetoleft', prod)" class="single_page_arrows" :href="'/singlepage/'+prod.id_product">
          <i class="fas fa-angle-left"></i>
        </button>
        <!-- <img alt="women" src="../img/single_page.png"> -->
        <img id="size" alt="women" :src="'../'+prod.img" />
        <button :disabled="$store.state.prodData.indexOf(prod)===$store.state.prodData.length-1" @click.prevent="$emit('slidetoright', prod)" class="single_page_arrows" :href="'/singlepage/'+prod.id_product">
          <i class="fas fa-angle-right"></i>
        </button>
      </div>
</template>

<script>
export default {
   name: 'carousel',
   props: {
      prod: Object,
      newProd: Object,
      products: Array,
      index: Number,
   }
}
</script>