<script setup>
const route = useRoute();
const { pending, data: product } = await useFetch(
  "https://erp.estorejamuna.com/api/products/" + route.params.slug
);
</script>

<template>
  <Head>
    <Title>{{ product.products.pro_name }}</Title>
    <Meta name="description" :content="product.products.pro_name" />
  </Head>
  <div class="container">
    <div class="col-lg-8 border p-3 main-section bg-white">
      <div class="row hedding m-0 pl-3 pt-0 pb-3">
        {{ product.products.pro_name }}
      </div>
      <div class="row m-0">
        <div class="col-lg-4 left-side-product-box pb-3">
          <img
            :src="
              `https://erp.estorejamuna.com` + product.products.feature_image
            "
            class="border p-3"
          />
        </div>
        <div class="col-lg-8">
          <div class="right-side-pro-detail border p-3 m-0">
            <div class="row">
              <div class="col-lg-12">
                <p class="m-0 p-0 price-pro">
                  $ {{ product.products.discount_price }}
                </p>
                <hr class="p-0 m-0" />
              </div>
              <div class="col-lg-12 pt-2">
                <h5>Product Detail</h5>
                <span v-html="product.products.pro_specification"> </span>
                <hr class="m-0 pt-2 mt-2" />
              </div>

              <div class="col-lg-12 mt-3">
                <div class="row">
                  <div class="col-lg-6 pb-2">
                    <a href="#" class="btn btn-danger w-100">Add To Cart</a>
                  </div>
                  <div class="col-lg-6">
                    <a href="#" class="btn btn-success w-100">Shop Now</a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
body {
  font-family: "Roboto Condensed", sans-serif;
  background-color: #f5f5f5;
}

.hedding {
  font-size: 20px;
  color: #ab8181`;
}

.main-section {
  position: absolute;
  left: 50%;
  right: 50%;
  transform: translate(-50%, 5%);
}

.left-side-product-box img {
  width: 100%;
}

.left-side-product-box .sub-img img {
  margin-top: 5px;
  width: 83px;
  height: 100px;
}

.right-side-pro-detail span {
  font-size: 15px;
}

.right-side-pro-detail p {
  font-size: 25px;
  color: #a1a1a1;
}

.right-side-pro-detail .price-pro {
  color: #e45641;
}

.right-side-pro-detail .tag-section {
  font-size: 18px;
  color: #5d4c46;
}

.pro-box-section .pro-box img {
  width: 100%;
  height: 200px;
}

@media (min-width: 360px) and (max-width: 640px) {
  .pro-box-section .pro-box img {
    height: auto;
  }
}
</style>