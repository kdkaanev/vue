<script>
export default {
  data() {
    return {
      isDay: true,
      cartProducts: [
{ id: 1, name: 'Smartphone', price:
499.99, quantity: 2 },
{ id: 2, name: 'Laptop', price: 999.99,
quantity: 1 },
{ id: 3, name: 'Headphones', price:
79.99, quantity: 3 },
{ id: 4, name: 'Tablet', price: 299.99,
quantity: 2 },
],
inventory: [
{
id: 1,
name: 'Electronics',
products: [
{ id: 1, name: 'Smartphone', price:
499.99, quantity: 2 },
{ id: 2, name: 'Laptop', price: 999.99,
quantity: 1 },
],
},
{
id: 2,
name: 'Audio',
products: [
{ id: 3, name: 'Headphones', price:
79.99, quantity: 3 },
],
},
],
bookInfo: {
title: 'The Magical Adventure',
author: 'John Smith',
genre: 'Fantasy',
publishedAt: '2023-07-15',
pages: 320,
rating: '★★★★☆',
},
rangeVariable: 15,


    };
  },
  methods: {

    onDayChange() {
      this.isDay = !this.isDay;
    },
  },
};
</script>

<template>
  <h1>HelloWorld</h1>
  <h2 v-if="isDay">
    It's sunny outside!
  </h2>
  <h2 v-else>
    It's dadrk
    outside!
  </h2>

    <template v-if="isDay">
  <h1>
  Welcome to My Awesome Page
  </h1>
  <p>
  Hello there! This is a cool Vue.js
  example.
  </p>
  <p>
  Let's explore some awesome features
  together!
  </p>
  </template>
  <p v-else>
  Click the button above to reveal the
exciting content!
</p>

    <button @click="onDayChange">
      Togle time
    </button>
<h2 v-show="isDay">
  THIS SHOULD BE HIDDEN WHEN IS DAY
</h2>
<h2>My products</h2>
<ul>
  <li v-for="(product, idx) in cartProducts" :key="`product-${idx}`">
    {{ product.name }} {{ product.price }} x {{ product.quantity }}
    <input type="text">

  </li>
</ul>
<h2>Products and  category</h2>
<ul>
  <li v-for="category in inventory" :key="`category-${category.id}`">
    <article>
      <h3>{{ category.name }}</h3>
      <ol>
        <li v-for="prod in category.products" :key="`prod-${prod.id}`">
          <p>{{ prod.name }} x {{ prod.quantity }}</p>
        </li>
      </ol>
    </article>


  </li>
</ul>

<h1>My book</h1>
<article>
  <p v-for="(value, key) in bookInfo" :key="`book-${value}`">

    <span>{{ key }}</span>: {{ value }}
  </p>
  
</article>
<u>
  <li v-for="number in rangeVariable">
    {{ number }}
  </li>
</u>
</template>


