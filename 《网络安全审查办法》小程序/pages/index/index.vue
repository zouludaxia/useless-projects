<template>
	<view>
		<!-- #ifndef MP-ALIPAY -->
		<swiper class="card-swiper" :class="dotStyle?'square-dot':'round-dot'" :indicator-dots="true" :circular="true"
		 :autoplay="true" interval="2500" duration="500" @change="cardSwiper" indicator-color="#8799a3"
		 indicator-active-color="#0081ff" @tap='Tolist'>
			<swiper-item v-for="(item,index) in swiperList" :key="index" :class="cardCur==index?'cur':''">
				<view class="swiper-item">
					<image :src="item.url" mode="aspectFill" v-if="item.type=='image'"></image>
					<video :src="item.url" autoplay loop muted :show-play-btn="false" :controls="false" objectFit="cover" v-if="item.type=='video'"></video>
				</view>
			</swiper-item>
		</swiper>
		<!-- #endif -->
		<view class="cu-timeline">
				<view class="cu-time">...</view>
				<view class="cu-item text-pink">
					
					<view class="bg-pink content">
						<text>《网络安全审查办法》(2022)\n于2021年11月16日国家互联网信息办公室2021年第20次室务会议审议通过，并经国家发展和改革委员会、工业和信息化部、公安部、国家安全部、财政部、商务部、中国人民银行、国家市场监督管理总局、国家广播电视总局、中国证券监督管理委员会、国家保密局、国家密码管理局同意，现予公布，自2022年2月15日起施行。</text>
					</view>
				</view>
				<view class="cu-item cur cuIcon-noticefill">
					<view class="content bg-green shadow-blur">
						<text>2021年8月20日，十三届全国人大常委会第三十次会议表决通过《中华人民共和国个人信息保护法》。个人信息保护法自2021年11月1日起施行。</text> 
					</view>
				</view>
				<view class="cu-item text-blue">
					<view class="bg-cyan content">
						<text>《中华人民共和国数据安全法》\n发布时间：2021年6月10日，生效时间2021年9月1日\n作为我国关于数据安全的首部律法，《数据安全法》的颁布与实施标志我国在数据安全领域有法可依，为各行业数据安全提供监管依据。</text>
					</view>
				</view>
				<view class="cu-item text-red cuIcon-attentionforbidfill">
					<view class="content bg-red shadow-blur">
						<text>2021年4月27日国务院第133次常务会议通过《关键信息基础设施安全保护条例》，自2021年9月1日起施行。</text>
					</view>
				</view>
				<view class="cu-item text-yellow">
					<view class="bg-yellow content">
						<text>《网络安全审查办法》\n发布时间：2020年4月,生效时间: 2020年6月1日\n关键信息基础设施运营者采购网络产品和服务，影响或可能影响国家安全的，应当按照《办法》进行网络安全审查。</text>
					</view>
				</view>
				<view class="cu-item text-grey cuIcon-evaluate_fill">
					<view class="content bg-grey shadow-blur">
						<text>《网络安全等级保护技术2.0版本》\n发布时间：2019年5月,生效时间：2019年12月\n提出了对云计算安全、移动互联网安全、物联网安全和工业控制系统安全扩展要求。为落实信息安全工作提出了新的要求。</text>
					</view>
				</view>
				<view class="cu-item text-blue">
					<view class="bg-blue content">
						<text>2018年9月15日《公安机关互联网安全监督检查规定》发布，于2018年11月1日正式实施。规定明确公安机关依法对互联网服务提供者和联网使用单位履行法律、行政法规规定的网络安全义务情况进行的安全监督检查的对象、内容和程序以及互联网服务提供者和联网使用单位的法律责任。</text>
					</view>
					<view class="bg-cyan content">
						<text>2016年11月，《中华人民共和国网络安全法》正式发布，并于2017年6月1日开始实施。强调了金融、能源、交通、电子政务等行业在网络安全等级保护制度的建设，是我国第一部网络空间管理方面的基础性法律。</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cardCur: 0,
				swiperList: [{
					id: 0,
					type: 'image',
					url: '/static/feng.png'
				}, {
					id: 1,
					type: 'image',
					url: '/static/feng1.jpg',
				}, {
					id: 2,
					type: 'image',
					url: '/static/feng2.jpg'
				}, {
					id: 3,
					type: 'image',
					url: '/static/feng3.jpg'
				},{
					id: 4,
					type: 'image',
					url: '/static/feng.png'
				}, {
					id: 5,
					type: 'image',
					url: '/static/feng1.jpg',
				}],
				dotStyle: false,
				towerStart: 0,
				direction: ''
			};
		},
		onLoad() {
			this.TowerSwiper('swiperList');
			// 初始化towerSwiper 传已有的数组名即可
		},
		
		methods: {
			Tolist(e){
				uni.navigateTo({
				    url: "/pages/list1/list1"
				});
			},
			DotStyle(e) {
				this.dotStyle = e.detail.value
			},
			// cardSwiper
			cardSwiper(e) {
				this.cardCur = e.detail.current
			},
			// towerSwiper
			// 初始化towerSwiper
			TowerSwiper(name) {
				let list = this[name];
				for (let i = 0; i < list.length; i++) {
					list[i].zIndex = parseInt(list.length / 2) + 1 - Math.abs(i - parseInt(list.length / 2))
					list[i].mLeft = i - parseInt(list.length / 2)
				}
				this.swiperList = list
			},

			// towerSwiper触摸开始
			TowerStart(e) {
				this.towerStart = e.touches[0].pageX
			},

			// towerSwiper计算方向
			TowerMove(e) {
				this.direction = e.touches[0].pageX - this.towerStart > 0 ? 'right' : 'left'
			},

			// towerSwiper计算滚动
			TowerEnd(e) {
				let direction = this.direction;
				let list = this.swiperList;
				if (direction == 'right') {
					let mLeft = list[0].mLeft;
					let zIndex = list[0].zIndex;
					for (let i = 1; i < this.swiperList.length; i++) {
						this.swiperList[i - 1].mLeft = this.swiperList[i].mLeft
						this.swiperList[i - 1].zIndex = this.swiperList[i].zIndex
					}
					this.swiperList[list.length - 1].mLeft = mLeft;
					this.swiperList[list.length - 1].zIndex = zIndex;
				} else {
					let mLeft = list[list.length - 1].mLeft;
					let zIndex = list[list.length - 1].zIndex;
					for (let i = this.swiperList.length - 1; i > 0; i--) {
						this.swiperList[i].mLeft = this.swiperList[i - 1].mLeft
						this.swiperList[i].zIndex = this.swiperList[i - 1].zIndex
					}
					this.swiperList[0].mLeft = mLeft;
					this.swiperList[0].zIndex = zIndex;
				}
				this.direction = ""
				this.swiperList = this.swiperList
			},
		}
	}
</script>

<style>
	.tower-swiper .tower-item {
		transform: scale(calc(0.5 + var(--index) / 5));
		margin-left: calc(var(--left) * 100upx - 150upx);
		z-index: var(--index);
	}
	page{
		background-color: #3d3d3d;
	}
</style>
