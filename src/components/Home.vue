<template>
	<div id="home">
		<h1>我是首页</h1>
		

		<div class="swiper-container swiper-container-horizontal" id="swiper-container2" style="width:480px;">
			<div class="swiper-wrapper" style="transform: translate3d(0px, 0px, 0px); transition-duration: 0ms;">
				<div class="swiper-slide active-nav swiper-slide-visible swiper-slide-active" style="width: 160px;">
					版块1</div>
				<div class="swiper-slide swiper-slide-visible swiper-slide-next" style="width: 160px;">
					版块2</div>
				<div class="swiper-slide swiper-slide-visible" style="width: 160px;">
					版块3</div>
				<div class="swiper-slide" style="width: 160px;">
					版块4</div>
				<div class="swiper-slide" style="width: 160px;">
					版块5</div>
				<div class="swiper-slide" style="width: 160px;">
					版块6</div>
				<div class="swiper-slide" style="width: 160px;">
					版块7</div>
				<div class="swiper-slide" style="width: 160px;">
					版块8</div>
			</div>
		</div>

		<div class="swiper-container swiper-container-horizontal" id="swiper-container3" style="width:480px;">
			<div class="swiper-wrapper" style="transform: translate3d(0px, 0px, 0px); transition-duration: 0ms;">
				<div class="swiper-slide blue-slide swiper-slide-active" style="width: 480px;height:200px">
					slider1</div>
				<div class="swiper-slide red-slide swiper-slide-next" style="width: 480px;height:200px">
					slider2</div>
				<div class="swiper-slide orange-slide" style="width: 480px;height:200px">
					slider3</div>
				<div class="swiper-slide blue-slide" style="width: 480px;height:200px">
					slider4</div>
				<div class="swiper-slide red-slide" style="width: 480px;height:200px">
					slider5</div>
				<div class="swiper-slide orange-slide" style="width: 480px;height:200px">
					slider6</div>
				<div class="swiper-slide blue-slide" style="width: 480px;height:200px">
					slider7</div>
				<div class="swiper-slide red-slide" style="width: 480px;height:200px">
					slider8</div>
			</div>
		</div>
	</div>
</template>

<script>
	import Swiper from 'swiper'

	export default {
		mounted(){
			var mySwiper2 = new Swiper('#swiper-container2',{
				watchSlidesProgress : true,
				watchSlidesVisibility : true,
				slidesPerView : 4,
				
				onTap: function(){
					mySwiper3.slideTo( mySwiper2.clickedIndex)
				}
			})
			

			var mySwiper3 = new Swiper('#swiper-container3',{

				onSlideChangeStart: function(){
					updateNavPosition()
				}

			})

			function updateNavPosition(){
				$('#swiper-container2 .active-nav').removeClass('active-nav');
				
				var activeNav = $('#swiper-container2 .swiper-slide').eq(mySwiper3.activeIndex).addClass('active-nav');

				if (!activeNav.hasClass('swiper-slide-visible')) {
			
					if (activeNav.index()>mySwiper2.activeIndex) {
			
						var thumbsPerNav = Math.floor(mySwiper2.width/activeNav.width())-1;
						mySwiper2.slideTo(activeNav.index()-thumbsPerNav);

					} else {

						mySwiper2.slideTo(activeNav.index())

					}	
				}
			}
		}		
	}


	
	
	
</script>

<style>
	.swiper-slide{
		color:#fff;
		line-height:200px;
		text-align:center;
		font-size:50px;
	}


	#swiper-container2 .swiper-slide{
		line-height:2 !important;
		color:#666 !important;
		font-size:14px !important;
		background:#eee !important;
	}


	#swiper-container2 .active-nav{
		background:rgba(55,55,55,.3) !important;
	}



	.blue-slide{
		background: #4390EE;
	}
	.red-slide {
		background: #CA4040;
	}
	.orange-slide {
		background: #FF8604;
	}
	.green-slide{
		background:#49a430;
	}
	.pink-slide{
		background:#973e76;
	}
	


</style>