<template>
  <div class="product">
    <h3>{{ product.title }}</h3>
    <p>Serial Number: {{ product.serialNumber }}</p>
    <p>Type: {{ product.type }}</p>
    <p>Specification: {{ product.specification }}</p>
    <p class="not-to-be-margined">Price: {{ formatPrice(product.price) }}</p>
    <img :src="product.photo" alt="Product Photo" class="product-photo"/>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  methods: {
    formatPrice(price) {
      const defaultPrice = price.find(p => p.isDefault);
      return `${defaultPrice.symbol === 'UAH' ? defaultPrice.value + ' ₴' : '$ ' + defaultPrice.value}`;
    },
  }
};
</script>

<style scoped>
.product {
  border: 1px solid #ccc;
  padding: 10px;
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  margin-bottom: 1rem;
}

.product-photo {
  width: 75%;
  height: 75%;
  max-height: 25dvh;
  align-self: center;
  object-fit: contain;
}

@media (max-width: 720px) {
  .product {
    gap: 0.1rem;
    margin-bottom: 0.5rem;
    font-size: 75%;
    line-height: 75%;
  }

  .product-photo {
    width: 50%;
    height: 50%;
  }
}
</style>