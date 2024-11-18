<template>
  <!-- FEATURED PRODUCT CARD SECTION START -->
  <div class="block block-products-carousel" data-layout="grid-5">
    <div class="container">
      <div class="section-header">
        <div class="section-header__body">
          <h2 class="section-header__title">Featured Products</h2>
          <div class="section-header__spring"></div>
          <div class="section-header__arrows">
            <div @click="prevSlide" class="arrow section-header__arrow section-header__arrow--prev arrow--prev">
              <button class="arrow__button" type="button"><i class="fa fa-chevron-left"></i></button>
            </div>
            <div @click="nextSlide" class="arrow section-header__arrow section-header__arrow--next arrow--next">
              <button class="arrow__button" type="button"><i class="fa fa-chevron-right"></i></button>
            </div>
          </div>
          <div class="section-header__divider"></div>
        </div>
      </div>
      <!-- <Carousel transition="500" :breakpoints="breakpoints" ref="featured">
        <Slide v-for="(featured, index) in featureds" :key="(featured, index)">
          <div @click="handleCardClick(featured.p_id)">
            <Card class="product-card product-card--layout--grid pb-2" style="width:16rem;"
              :id="featured.p_id"
              :name="featured.p_name"
              :image="featured.p_image"
            />
          </div>
        </Slide>
      </Carousel> -->


      <Carousel transition="500" :breakpoints="breakpoints" ref="featured">
						<Slide v-for="(featured, index) in featureds" :key="(featured, index)">
							<div @click="handleCardClick(featured.p_id)">
								<Card class="product-card product-card--layout--grid pb-2 " style="width:16rem;"
									:id="featured.p_id" :name="featured.p_name" :image="featured.p_image" />
							</div>

						</Slide>
					</Carousel>
    </div>
  </div>
  <!-- FEATURED PRODUCT CARD SECTION END -->

  <!-- Modal -->
  <div class="modal fade" tabindex="-1" role="dialog" :class="{ show: showModal }"
    :style="showModal ? 'display: block; background-color: rgba(0,0,0,0.5)' : 'display: none'">
    <div class="modal-dialog modal-dialog-centered" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" @click="closeModal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          Do you want to see more products? If yes, please go to the login page to view the details.
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" @click="closeModal">Close</button>
          <a href="/login" type="button" class="btn btn-danger">Login</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { Url } from '~/config/url';

export default {
  data() {
    return {
      showModal: false,
      featureds: [],
    };
  },
  methods: {
    async fetchCategory() {
      try {
        const response = await axios.get(Url.fetchHomeCategory);
        if (response.data.productArray) {
          this.featureds = response.data.productArray;
        }
      } catch (error) {
        console.error('Error fetching categories:', error);
      }
    },
    handleCardClick(id) {
      const token = localStorage.getItem('authToken');
      if (token) {
        window.location.href = `/product/${id}/`;
      } else {
        this.showModal = true;
      }
    },
    closeModal() {
      this.showModal = false;
    },
  },
  mounted() {
    this.fetchCategory();
  },
};
</script>
