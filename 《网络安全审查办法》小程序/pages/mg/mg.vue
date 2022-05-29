<template>
	<view>
		<view class="padding text-center">
			<view class="padding-l radius shadow-warp bg-white margin-top">
				<image src="/static/审查办法1.gif"></image>
			</view>
		</view>
		<view class="cu-list menu card-menu margin-top-xl margin-bottom-xl shadow-lg">
			<view class="cu-item arrow" v-for="(item,index) in 23" :key="index" @tap='Topage(index)'>
				<view class="content">
					<text class="cuIcon-magic text-blue"></text>
					<text class="text-cyan">第{{index +1}}条：</text>
					<text class="text-purple">{{point[index]}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				point:[
					'目的及依据',
					'当事人范围',
					'审查的要求',
					'相关部门',
					'关基运营者应预判风险',
					'关基运营者配合审查',
					'网络平台运营者赴国外上市',
					'申报审查需提交的材料',
					'确定审查必要性的时限',
					'重点评估的国家安全风险因素',
					'完成初步审查的时限',
					'审查结论建议的处理',
					'特别审查程序',
					'特别审查程序的时限',
					'补充材料的提交',
					'成员单位认为需要审查',
					'知识产权保护及其他保密义务',
					'审查的救济方式',
					'当事人的督促义务',
					'法律后果及处理依据',
					'网络产品和服务的含义',
					'规定条款竞合的处理',
					'正式实施的时间'
				]
			}
		},
		methods: {
			Topage(e){
				console.log(e)
				uni.navigateTo({  
				    url: '/pages/content/content?id=' + e
				});
			}
		}
	}
</script>

<style>

</style>
