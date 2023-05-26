<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inventory > 10">In Stock</p>
            <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out!</p>
            <p v-else>Out of Stock</p>
            <ul>
              <li v-for=" (detail, index) in details" :key="index">{{ detail }}</li>
            </ul>
            <ul>
              <li v-for="(size, index) in sizes" :key="index">{{ size }}</li>
            </ul>
            <div v-for="variant in variants" :key="variant.id" @mouseover="updateImage(variant.image)">{{ variant.color }}</div>
            <button class="button" v-on:click="addToCart">Add to Cart</button>
      </div>
    </div>
  </div>
</template>

<script>
import Bluesocks from '../assets/socks_blue.jpg'
import Greensocks from '../assets/socks_green.jpg'

export default {
  name: "SkillAll",
  data() {
    return {
      cart: 0,
      product: "Socks",
      image: Bluesocks,
      inventory:100,
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
              { id: 2234, color: 'green', image: Greensocks },
              { id: 2235, color: 'blue', image: Bluesocks  },
            ],
            sizes: ['S', 'M', 'L', 'XL']
    }
  },
    methods: {
      addToCart() {
            this.cart += 1
        },
        updateImage(variantImage) {
            this.image = variantImage
        }
    }
  
};


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 25px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.57);
}

.product-display {
  display: flex;
  flex-direction: column;
  padding: 1rem;
}

.product-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

img {
  border: 2px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  padding: 15px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 2px 15px -12px rgba(0, 0, 0, 0.57);
}

h1 {
  font-size: 50px;
}

h3 {
  font-size: 25px;
}

p {
  font-size: 22px;
}

.product-image,
.product-info {
  width: 50%;
}
</style>
