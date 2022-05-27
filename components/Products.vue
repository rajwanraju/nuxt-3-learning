<template>
  <div class="container">
    <div class="home-tab" v-show="!pending">
      <div class="tab-title text-left">
      </div>
      <div id="productTabContent" class="tab-content">
        <div class="tab-pane active in" id="computer">
          <div class="featured-pro">
            <div class="slider-items-products">
              <div id="computer-slider" class="product-flexslider hidden-buttons">
                <div class="slider-items slider-width-col4">
                      <div class="product-item" v-for="(slide, i) in products.products" :key="i">
                        <div class="item-inner">
                      
                          <div class="product-thumbnail">
                            
                             <div class="icon-sale-label" v-show="slide.discount_amount != 0">
                             <div class='ribbon ribbon--red'>
                              <span v-if="slide.discount_type == 2">{{slide.discount_amount}}%</span>
                            <span v-else>Tk {{slide.discount_amount}}</span>
                            <br>
                            Off
                              </div>
                          
                          </div>
                              <div class="icon-stock-ribbon stock-ribbon"  v-show="slide.pro_quantity <= 0">
                              Out Of Stock
                            </div>
                            <div class="pr-img-area">
                               <nuxt-link
                              :to="{path:'/product/'+slide.slug}"
                              :title="slide.pro_name"
                              :style="{ cursor: 'pointer','text-decoration':'none'}">
                                <figure>
                                  <img
                                    class="first-img"
                                    :src="`https://erp.estorejamuna.com`+slide.thumb_image"
                                    :alt="slide.pro_name"
                                  />
                                  
                                </figure>
                                </nuxt-link>
                            </div>
                            <div class="pr-info-area">
                              <div class="pr-button">
                                <div class="mt-button add_to_wishlist">
                                  <a title="Wishlist" @click="addToWish(slide)">
                                    <i class="fa fa-heart" aria-hidden="true"></i>
                               
                                  </a>
                                </div>

                                <div class="mt-button add_to_compare">
                                  <a @click="compairProduct(slide)" title="Compare">
                                    <i class="fa fa-link"></i>
                        

                                  </a>
                                </div>
                              </div>
                            </div>
                          </div>
                          <div class="item-info">
                            <div class="info-inner">
                                  <div class="item-title link">
                           {{slide.pro_name}}
                          </div>
                              <div class="item-content row">
                                <div class="item-price col-sm-6">
                                  <div class="price-box" v-if="slide.discount_amount != 0">
                                     <p class="special-price">
                                      <span class="price-label">Special Price</span>
                                      <span class="price">Tk {{(slide.discount_price)}}</span>
                                    </p> 
                                    <p class="old-price">
                                      <span class="price-label">Regular Price:</span>
                                      <span class="price">Tk {{(slide.regular_price)}}</span>
                                    </p>
                                   
                                  </div>
                                  <div class="price-box" v-else>
                                     <p class="special-price">
                                      <span class="price-label">Regular Price</span>
                                      <span class="price">Tk {{(slide.discount_price)}}</span>
                                    </p> 
                                  </div>
                                </div>
                                <div class="cart-btn col-sm-6" v-show="slide.pro_quantity > 0">
                                  <button
                                    type="button"
                                    class="add-to-cart"
                                    @click="addToCard(slide)"
                                  >
                                    <span>
                                      <i class="fa fa-shopping-cart"></i> 
                 

                                      Add
                                    </span>
                                  </button>
                                </div>
                              </div>
                            </div>
                          </div>
                        </div>
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

<script setup>
const { pending,data: products } = await useLazyFetch('https://erp.estorejamuna.com/api/category-slider/61');
watch(products, (newPosts) => {
console.log(newPosts);
})
</script>