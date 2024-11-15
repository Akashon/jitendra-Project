<template>
	
	<div class="block block-posts-carousel block-posts-carousel--layout--grid" data-layout="grid">
		<div class="container">
			<div class="section-header">
				<div class="section-header__body">
					<h2 class="section-header__title">Latest News</h2>
					<div class="section-header__spring"></div>
					<div class="section-header__arrows">
						<div @click="exThreePrevSlide"
							class="arrow section-header__arrow section-header__arrow--prev arrow--prev">
							<button class="arrow__button" type="button"><i class="fa fa-chevron-left"></i></button>
						</div>
						<div @click="exThreeNextSlide"
							class="arrow section-header__arrow section-header__arrow--next arrow--next">
							<button class="arrow__button" type="button"><i class="fa fa-chevron-right"></i></button>
						</div>
					</div>
					<div class="section-header__divider"></div>
				</div>
			</div>
			<!-- CARD SECTION START -->
			<div class="container my-4">
				<Carousel lass="block-posts-carousel__carousel row" transition="500"
					:breakpoints="breakpointsExtraProduct" :touchDrag="true" ref="extraThreeProduct">
					<Slide class="col-lg-3 col-md-4 col-sm-6 mb-4"  v-for="card in cards" :key="card.id">
						<div class="block-posts-carousel__item ">
							<div class="post-card shadow">
								<div class="post-card__image">
									<a href="/"><img :src="card.image" alt=""></a>
								</div>
								<div class="post-card__content" style="text-align: start;">
									<div class="post-card__category">
										<a href="/">{{ card.title }}</a>
									</div>
									<div class="post-card__title">
										<h2><a href="/">{{ card.excerpt }}</a></h2>
									</div>
								</div>
							</div>
						</div>
					</Slide>
				</Carousel>
			</div>
			<!-- CARD SECTION START -->
		</div>
	</div>
</template>



<script>
export default {
	data() {
		return {
			cards: [
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-2-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit...',
					link: 'post-full-width.html'
				},
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-3-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Donec facilisis neque ut purus fermentum...',
					link: 'post-full-width.html'
				},
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-5-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Suspendisse tempor orci non sapien ullamcorper...',
					link: 'post-full-width.html'
				},
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-1-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Vivamus venenatis viverra iaculis non sapie...',
					link: 'post-full-width.html'
				},
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-4-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Suspendisse tempor orci non sapien ullamcorper...',
					link: 'post-full-width.html'
				},
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-5-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Vivamus venenatis viverra iaculis viverra iaculis...',
					link: 'post-full-width.html'
				}
				,
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-6-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Suspendisse tempor orci non sapien ullamcorper...',
					link: 'post-full-width.html'
				},
				{
					image: 'https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/posts/post-3-730x485.jpg',
					title: 'Latest Title',
					excerpt: 'Vivamus venenatis viverra iaculis viverra iaculis...',
					link: 'post-full-width.html'
				}
			],

			breakpointsExtraProduct: {
				375: { itemsToShow: 1, snapAlign: "center" },
				// 700px and up
				700: { itemsToShow: 2, snapAlign: "center" },
				// 1024 and up
				1024: { itemsToShow: 4, snapAlign: "start" },
				// 1880 and up
				1880: { itemsToShow: 4, snapAlign: "start" }
			},


		};
	},
	methods: {

		exThreePrevSlide() {
			this.$refs.extraThreeProduct.prev();
		},
		exThreeNextSlide() {
			this.$refs.extraThreeProduct.next();
		},
		// RELATED PROUDCT NEXT AND PREVIEW SLIDE BUTTON END

		lNPrevSlide() {
			this.$refs.extraProduct.prev();
		},
		lNNextSlide() {
			this.$refs.extraProduct.next();
		},
	},

}
</script>

<style scoped>
.card {
	border: none;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>