<template>
	<view>
		<view class="top-part">
			<view class="list" v-for="item in items" :key="item.key">
				填充上半部分
			</view>
		</view>
		<view class="line-wapper" :class="{fix:isFix}" :style="'top:'+barHeight+'px'">
			<view class="suspension-line" id="suspension-line">
			<view class="part">品质联盟</view>
			<view class="part">满减优惠</view>
			<view class="part">配送费优惠</view>
			<view class="part">新店</view>
		</view>
		</view>
		
		<view class="top-part">
			<view class="list" v-for="item in items" :key="item.key">
				填充下半部分
			</view>
		</view>
	</view>
</template>

<script>
	var selectorQuery = null;
	export default {
		data() {
			return {
				barHeight:0,
				isFix:false,
				items:[]
			}
		},
		onLoad() {
			this.barHeight = uni.getSystemInfoSync().windowTop || uni.getSystemInfoSync().statusBarHeight;
			for (var i = 0; i < 50; i++) {
				var item = {key:i,value:i};
				this.items.push(item);
			}
		},
		onReady() {
			selectorQuery = uni.createSelectorQuery();
		},
		onPageScroll() {
			selectorQuery.select('.top-part').boundingClientRect((nodeInfo) => {
				if(nodeInfo.bottom-this.barHeight <= 0){
					this.isFix = true;
				}else{
					this.isFix = false;
				}
			}).exec();
		},
		methods: {
		}
	}
</script>

<style>
.fix{
	position: fixed;
	top: 0upx;
}
.line-wapper{
	width: 100%;
}
.suspension-line{
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	margin: 0upx 20upx;
}
.part{
	background-color: #d4cfcf;
	padding: 10upx;
}
</style>
