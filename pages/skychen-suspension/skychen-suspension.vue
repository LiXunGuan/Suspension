<template>
	<view>
		<view id="top-part" class="top-part">
			<view class="list" v-for="item in items" :key="item.key">
				填充第一部分
			</view>
		</view>
		<skychenSuspension :disHeight="dis1" preClass="top-part" ref="suspension_0">
			<view class="part">品质联盟</view>
			<view class="part">满减优惠</view>
			<view class="part">配送费优惠</view>
			<view class="part">新店</view>
		</skychenSuspension>
		<view class="bottom-part">
			<view class="list" v-for="item in items" :key="item.key">
				填充第二部分
			</view>
		</view>
		<skychenSuspension :disHeight="dis2" preClass="bottom-part" ref="suspension_1">
			<view class="part">品质联盟</view>
			<view class="part">满减优惠</view>
			<view class="part">配送费优惠</view>
			<view class="part">新店</view>
		</skychenSuspension>
		<view class="bottom-part2">
			<view class="list" v-for="item in items" :key="item.key">
				填充第三半部分
			</view>
		</view>
	</view>
</template>

<script>
	var selectorQuery = null;
	import skychenSuspension from '../../components/skychen-suspension.vue'
	export default {
		components: {
			skychenSuspension
		},
		data() {
			return {
				items: [],
				dis1:0,
				dis2:39
			}
		},
		onLoad() {
			
			for (var i = 0; i < 50; i++) {
				var item = {
					key: i,
					value: i
				};
				this.items.push(item);
			}
		},
		onReady() {
			selectorQuery = uni.createSelectorQuery();
		},
		onPageScroll() {
			this.$refs.suspension_0.pageScroll();
			this.$refs.suspension_1.pageScroll();
		},
		methods: {
		}
	}
</script>

<style>
	.part {
		background-color: #d4cfcf;
		padding: 10upx;
	}
</style>
