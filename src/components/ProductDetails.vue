<template>
  <div class="products">
    <div v-for="(product, index) in products" :key="index" class="product">
      <div class="product__image">
        <img :src="product.image" :alt="alt" />
      </div>
      <div class="product__data">
        <h1>{{ product.name }}</h1>
        <h2 v-if="product.available">Available</h2>
        <h2 v-else>Out of Stock</h2>
        <p>Price: {{ formattedPrice(index) }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDetails",
  data() {
    return {
      products: [
        {
          name: "Kitchen 1",
          price: "4,000",
          available: true,
          image: require("../assets/card1.svg"),
        },
        {
          name: "Kitchen 2",
          price: "4,400",
          available: true,
          image: require("../assets/card2.svg"),
        },
        {
          name: "Kitchen 3",
          price: "5,000",
          available: false,
          image: require("../assets/card3.svg"),
        },
        {
          name: "Kitchen 4",
          price: "2,800",
          available: false,
          image: require("../assets/card4.svg"),
        },
      ],
    };
  },

  methods: {
    formattedPrice(index) {
      return `$${this.products[index].price}`;
    },
  },
};
</script>

<style lang="css" scoped>
.products {
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
}

.product {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  border: 5px solid rgba(109, 145, 134, 0.288);
  border-radius: 10px;
  background-color: #e2ede9;
  padding: 10px;
}
.product__data {
  color: rgb(10, 92, 65);
}
</style>
