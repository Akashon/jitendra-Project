<template>
    <div class="block-split__item block-split__item-content col-auto">
        <div class="product product--layout--full">
            <div class="product__body">
                <!-- IMAGE SECTION START -->
                <div class="product-gallery product-gallery--layout--product-full product__gallery"
                    data-layout="product-full">
                    <div class="product-gallery__featured">
                        <button type="button" class="product-gallery__zoom">
                            <i class="fa-solid fa-magnifying-glass-plus" style="font-size: 32px;"></i>
                        </button>
                        <div class="owl-carousel">
                            <a class="image image--type--product" href="" target="_blank" data-width="700"
                                data-height="700">
                                <div class="image__body"><img class="image__tag" :src="activeImage.small"
                                        :alt="activeImage.alt"></div>
                            </a>
                        </div>
                    </div>
                    <div class="row"
                        style="display: flex; justify-content: space-between; align-items: center; ">
                        <i @click="prev" :disabled="isFirstPage" class="fa fa-chevron-left"
                            style="color: red; background-color: red; padding: 6px; font-size: 20px; color: white; border-radius: 4px;"></i>

                        <div v-for="(image, index) in visibleImages" :key="index" class="col-2">
                            <img width="55" height="60" :src="image.small" :alt="image.alt" class=""
                                :class="{ 'active-thumbnail': activeIndex === index + startIndex }"
                                @click="changeImage(index + startIndex)" />
                        </div>

                        <i @click="next" :disabled="isLastPage" class="fa fa-chevron-right"
                            style="color: red; background-color: red; padding: 6px; font-size: 20px; color: white; border-radius: 4px;"></i>
                    </div>
                </div>
                <!-- IMAGE SECTION END -->

                <div class="product__header">
                    <h1 class="product__title" style="font-size: 30px;">{{ name }}</h1>
                    <div class="product__subtitle">
                        <h6 style="background-color: #E2F2DA; font-weight: lighter; font-size: 14px; border-radius: 12px; align-items: center; font-weight: 400;"
                            class="px-2 py-1 mt-1"><i class="fa fa-check pr-1"></i>Drow No. AEG2013
                        </h6>
                        <div class="product__rating mt-1">
                            <div class="product__rating-stars">
                                <div class="rating">
                                    <div class="rating__body">
                                        <div class="rating__star rating__star--active"></div>
                                        <div class="rating__star rating__star--active"></div>
                                        <div class="rating__star rating__star--active"></div>
                                        <div class="rating__star rating__star--active"></div>
                                        <div class="rating__star"></div>
                                    </div>
                                </div>
                            </div>
                            <div class="product__rating-label"><a href="#">3.5 on 7 reviews</a></div>
                        </div>
                    </div>
                </div>

                <div class="product__main">
                    <div class="product__excerpt" style="font-weight: 400; font-size: 17px;">SS Cabinet, or stainless
                        steel cabinet, is a durable
                        and rust-resistant storage solution commonly used in kitchens, laboratories, and
                        industrial spaces. Its sleek, modern design offers both functionality and
                        aesthetic appeal.
                    </div>
                    <div class="product__features">
                        <div class="product__features-title" style="font-weight: 600; font-size: 18px;">Key Features:
                        </div>
                        <ul class="" style="align-items: center;">
                            <li style="font-size: 17px; ">Brand: <span>Advance...</span></li>
                            <li style="font-size: 17px;">Material: <span>550304</span></li>
                            <li style="font-size: 17px;">product dimensions: <span>L-300mm, W-500mm, H-600mm</span></li>
                            <li style="font-size: 17px;">Finish Type: <span>Mi.... Matt</span></li>
                            <!-- <li>Battery Capacity: <span>2 Ah</span></li> -->
                        </ul>
                    </div>
                </div>

                <div class="product__info">
                    <div class="product__info-card">
                        <div class="product__info-body">
                            <div class="product__prices-stock">
                                <div class="product__prices">
                                    <div class="product__price product__price--current">1,499.00</div>
                                </div>
                                <div
                                    class="status-badge status-badge--style--success product__stock status-badge--has-text">
                                    <div class="status-badge__body">
                                        <div class="status-badge__text">In Stock</div>
                                        <div class="status-badge__tooltip" tabindex="0" data-toggle="tooltip"
                                            title="In&#x20;Stock"></div>
                                    </div>
                                </div>
                            </div>
                            <div class="product__meta">
                                <table>
                                    <tr>
                                        <th style="font-size: 16px;">Brand </th>
                                        <td style="font-size: 16px;">Bosch</td>
                                    </tr>
                                    <tr>
                                        <th style="font-size: 16px;">Material</th>
                                        <td style="font-size: 16px;"><a href="#">550304</a></td>
                                    </tr>
                                    <tr>
                                        <th style="font-size: 16px;">Product Dimensions</th>
                                        <td style="font-size: 16px;">31L, 12W, 9.2H Centimeters</td>
                                    </tr>
                                    <tr>
                                        <th style="font-size: 16px;">Style</th>
                                        <td style="font-size: 16px;">GWS 600</td>
                                    </tr>
                                    <tr>
                                        <th style="font-size: 16px;">Power Source </th>
                                        <td style="font-size: 16px;">Carded Electric</td>
                                    </tr>
                                    <tr>
                                        <th style="font-size: 16px;">Color</th>
                                        <td style="font-size: 16px;">Silver</td>
                                    </tr>
                                    <tr>
                                        <th style="font-size: 16px;">Item Width</th>
                                        <td style="font-size: 16px;">1905 Grams</td>
                                    </tr>
                                </table>
                            </div>
                        </div>
                        <div class="product-form product__form">
                            <div class="product-form__body">
                                <div class="product-form__row">
                                    <div class="product-form__title">Material</div>
                                    <div class="product-form__control">
                                        <div class="input-radio-label">
                                            <div class="input-radio-label__list"><label class="input-radio-label__item">
                                                    <input type="radio" name="material"
                                                        class="input-radio-label__input"> <span
                                                        class="input-radio-label__title">Steel</span></label>
                                                <label class="input-radio-label__item"><input type="radio"
                                                        name="material" class="input-radio-label__input"> <span
                                                        class="input-radio-label__title">Aluminium</span></label>
                                                <label class="input-radio-label__item"><input type="radio"
                                                        name="material" class="input-radio-label__input"> <span
                                                        class="input-radio-label__title">Thorium</span></label>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="product__actions">
                            <div class="product__actions-divider"></div><button
                                class="product__actions-item product__actions-item--wishlist" type="button"><i
                                    class="fa fa-heart mr-2" style="color: #BFBFBF;"></i>
                                <span>Add to wishlist</span></button> <button
                                class="product__actions-item product__actions-item--compare" type="button"><i
                                    class="fa fa-bar-chart mr-2" style="color: #BFBFBF;"></i> <span>Add to
                                    compare</span></button>
                        </div>
                    </div>
                    <div class="product__shop-features shop-features">
                        <ul class="shop-features__list">
                            <li class="shop-features__item" v-for="cont in conts">
                                <div class="shop-features__item-icon"><img width="75" :src="cont.image" alt=""></div>
                                <div class="shop-features__info">
                                    <div class="shop-features__item-title " style="font-size: 16px;">{{ cont.name }}
                                    </div>
                                    <div class="shop-features__item-subtitle">{{ cont.subName }}</div>
                                </div>
                            </li>
                            <li class="shop-features__divider" role="presentation"></li>
                        </ul>
                    </div>
                </div>

                <div class="product__tabs product-tabs product-tabs--layout--full">
                    <ul class="nav nav-tabs product-tabs__list" role="tablist">
                        <li class="product-tabs__item"
                            :class="{ 'product-tabs__item--active': activeTab === 'tabs-1' }">
                            <a style="font-size: 18px;" class="nav-link" @click.prevent="setActiveTab('tabs-1')"
                                href="#tabs-1" role="tab">
                                Description
                            </a>
                        </li>
                        <li class="product-tabs__item"
                            :class="{ 'product-tabs__item--active': activeTab === 'tabs-2' }">
                            <a style="font-size: 18px;" class="nav-link" @click.prevent="setActiveTab('tabs-2')"
                                href="#tabs-2" role="tab">
                                Specification
                            </a>
                        </li>
                        <li class="product-tabs__item"
                            :class="{ 'product-tabs__item--active': activeTab === 'tabs-3' }">
                            <a style="font-size: 18px;" class="nav-link" @click.prevent="setActiveTab('tabs-3')"
                                href="#tabs-3" role="tab">
                                Reviews
                            </a>
                        </li>
                        <li class="product-tabs__item"
                            :class="{ 'product-tabs__item--active': activeTab === 'tabs-4' }">
                            <a style="font-size: 18px;" class="nav-link" @click.prevent="setActiveTab('tabs-4')"
                                href="#tabs-4" role="tab">
                                Analogs
                            </a>
                        </li>
                    </ul>
                    <!-- Tabs Content -->
                    <!-- Tab panes -->
                    <div class="tab-content">
                        <div class="tab-pane p-3" :class="{ active: activeTab === 'tabs-1' }" id="tabs-1"
                            role="tabpanel">
                            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas
                                fermentum, diam non iaculis finibus, ipsum arcu sollicitudin dolor, ut
                                cursus sapien sem sed purus. Donec vitae fringilla tortor, sed fermentum
                                nunc. Suspendisse sodales turpis dolor, at rutrum dolor tristique id.
                                Quisque pellentesque ullamcorper felis, eget gravida mi elementum a.
                                Maecenas consectetur volutpat ante, sit amet molestie urna luctus in.
                                Nulla eget dolor semper urna malesuada dictum. Duis eleifend
                                pellentesque dui et finibus. Pellentesque dapibus dignissim augue. Etiam
                                odio est, sodales ac aliquam id, iaculis eget lacus. Aenean porta, ante
                                vitae suscipit pulvinar, purus dui interdum tellus, sed dapibus mi
                                mauris vitae tellus.</p>
                        </div>
                        <div class="tab-pane p-3" :class="{ active: activeTab === 'tabs-2' }" id="tabs-2"
                            role="tabpanel">
                            <p>Second Panel</p>
                        </div>
                        <div class="tab-pane p-3" :class="{ active: activeTab === 'tabs-3' }" id="tabs-3"
                            role="tabpanel">
                            <p>Third Panel</p>
                        </div>
                        <div class="tab-pane p-3" :class="{ active: activeTab === 'tabs-4' }" id="tabs-4"
                            role="tabpanel">
                            <p>Third Panel</p>
                        </div>
                    </div>
                </div>

            </div>
        </div>
        <div class="block-space block-space--layout--divider-nl"></div>
        <!-- Related Products start -->
        <div class="block block-products-carousel" data-layout="grid-5">
            <div class="container">
                <div class="section-header">
                    <div class="section-header__body">
                        <h2 class="section-header__title">Related Products</h2>
                        <div class="section-header__spring"></div>
                        <div class="section-header__arrows">
                            <div @click="prevSlide"
                                class="arrow section-header__arrow section-header__arrow--prev arrow--prev">
                                <button class="arrow__button" type="button"><i class="fa fa-chevron-left"></i></button>
                            </div>
                            <div @click="nextSlide"
                                class="arrow section-header__arrow section-header__arrow--next arrow--next">
                                <button class="arrow__button" type="button"><i class="fa fa-chevron-right"></i></button>
                            </div>
                        </div>
                        <div class="section-header__divider"></div>
                    </div>
                </div>
                <Carousel transition="1500" :breakpoints="breakpoints" :wrap-around="true" :touchDrag="true"
                    ref="related">
                    <Slide>
                        <Card />
                    </Slide>
                </Carousel>
            </div>
        </div>
        <!-- Related Products end -->
    </div>
</template>
<script>
export default {
    data() {
        return {
            conts: [
                { image: "https://png.pngtree.com/png-clipart/20230120/ourmid/pngtree-free-delivery-truck-icon-png-image_6565580.png", name: "Free Shipping", subName: "For orders from $50" },
                { image: "https://static.vecteezy.com/system/resources/previews/016/314/360/non_2x/transparent-24-hour-service-free-png.png", name: "Support 24/7", subName: "Call us anytime" },
                { image: "https://png.pngtree.com/png-vector/20221009/ourmid/pngtree-original-guaranteed-stamp-and-badget-design-red-grunge-png-image_6293839.png", name: "100% Safety", subName: "Only secure payments" },
                { image: "https://png.pngtree.com/png-vector/20240417/ourmid/pngtree-fire-icon-vector-design-png-image_12288010.png", name: "Hot Offers", subName: "Discounts up to 90%" },

            ],

            breakpoints: {
                375: { itemsToShow: 1, snapAlign: "center" },
                // 700px and up
                700: { itemsToShow: 2, snapAlign: "center" },
                // 1024 and up
                1024: { itemsToShow: 1, snapAlign: "start" },
            },
            activeIndex: 0, // First image is active by default
            startIndex: 0,   // Index to keep track of the current visible set of images
            images: [
                {
                    small: "https://png.pngtree.com/png-vector/20240203/ourmid/pngtree-steel-cabinet-furniture-wooden-with-separate-storage-drawers-on-a-white-png-image_11593718.png",
                    alt: "Product Image 1",
                },
                {
                    small: "https://png.pngtree.com/png-vector/20231006/ourmid/pngtree-versatile-steel-cabinet-ideal-for-factories-schools-gyms-png-image_10079349.png",
                    alt: "Product Image 2",
                },
                {
                    small: "https://www.furnituremanila.com.ph/wp-content/uploads/2023/09/bf02-filing-cabinet-3.png",
                    alt: "Product Image 3",
                },
                {
                    small: "https://m.media-amazon.com/images/I/61j5e65xNEL._AC_UF1000,1000_QL80_.jpg",
                    alt: "Product Image 4",
                },
                {
                    small: "https://f31.sg/wp-content/uploads/2018/06/products-lm13.jpg",
                    alt: "Product Image 5",
                },
                {
                    small: "https://i.ebayimg.com/images/g/P4wAAOSw91pcr1nF/s-l1200.jpg",
                    alt: "Product Image 6",
                },
            ],
            activeTab: 'description' // Default active tab
        };
    },
    props: {
        id: {
      default: "",
    },
    name: {
      default: "",
    },
    },
    methods: {
        changeImage(index) {
            // Update the active image when a thumbnail is clicked
            this.activeIndex = index;
        },
        next() {
            // Go to the next set of images
            if (!this.isLastPage) {
                this.startIndex += 1;
                if (this.startIndex + 3 > this.images.length) {
                    this.startIndex = this.images.length - 3; // Adjust to last set
                }
            }
        },
        prev() {
            // Go to the previous set of images
            if (!this.isFirstPage) {
                this.startIndex -= 1;
                if (this.startIndex < 0) {
                    this.startIndex = 0; // Adjust to first set
                }
            }
        },

        setActiveTab(tabName) {
            this.activeTab = tabName;
        },

        // RELATED PROUDCT NEXT AND PREVIEW SLIDE BUTTON START 
        prevSlide() {
            this.$refs.related.prev();
        },
        nextSlide() {
            this.$refs.related.next();
        },
        // RELATED PROUDCT NEXT AND PREVIEW SLIDE BUTTON END 

    },

    computed: {
        activeImage() {
            // Returns the currently active image based on activeIndex
            return this.images[this.activeIndex];
        },
        visibleImages() {
            // Returns the currently visible set of images based on startIndex
            return this.images.slice(this.startIndex, this.startIndex + 3);
        },
        isFirstPage() {
            return this.startIndex === 0;
        },
        isLastPage() {
            return this.startIndex + 3 >= this.images.length;
        },
    },
};
</script>

<style scoped>
/* Main image styling */
.main-image img {
    max-height: 400px;
    object-fit: contain;
    width: 100%;
}

/* Thumbnail image styling */
.img-thumbnail {
    transition: border 0.3s ease-in-out;
}

/* Highlight the active thumbnail */
.active-thumbnail {
    border: 2px solid #007bff;
}

/* Button styling */
.btn {
    margin: 0 10px;
}

.product-tabs__item--active a {
    font-weight: 700;
    /* Example for active tab styling */
}
</style>