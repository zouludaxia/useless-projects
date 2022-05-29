<template>
	<view>
		<view class="padding text-center">
			<view class="padding-xl radius shadow-warp bg-mask margin-top">
				<!-- <view class="cu-avatar xl round margin-center" style="background-image:url(/static/avatar.jpg)"> -->
					<image src="/static/avatar.jpg"></image>
				<!-- </view> -->
				<text class="text-white">\n作者：乐乐</text>
			</view>
		</view>

		<view class="cu-list menu" :class="[menuBorder?'sm-border':'',menuCard?'card-menu margin-top':'']">
			<view class="cu-item" :class="menuArrow?'arrow':''">
				<view class="content">
					<text class="cuIcon-circlefill text-grey"></text>
					<text class="text-grey">作者联系方式 1051434511@qq.com</text>
				</view>
			</view>
			<view class="cu-item" :class="menuArrow?'arrow':''">
				<button class="cu-btn content" @tap="showModal" data-target="menuModal">
					<text class="cuIcon-paint text-purple"></text>
					<text class="text-grey">作者个性签名</text>
				</button>
			</view>
			<view class="cu-modal" :class="modalName=='menuModal'?'show':''" @tap="hideModal">
				<view class="cu-dialog" @tap.stop>
					<view class="cu-list menu text-center solid-top">
						<!-- <view class="padding text-left"> -->
							<view class="padding-xl radius shadow-warp bg-white margin-top">
								<text>"亭亭玉立，两袖清风。\n花拳绣腿，一事无成。"</text>
							</view>
						<!-- </view> -->
					</view>
				</view>
			</view>
			<view class="cu-item" :class="menuArrow?'arrow':''">
				<button class="cu-btn content" @tap="showModal" data-target="menuModal1">
					<text class="cuIcon-emojiflashfill text-pink"></text>
					<text class="text-grey">团队</text>
				</button>
			</view>
			<view class="cu-modal" :class="modalName=='menuModal1'?'show':''" @tap="hideModal">
				<view class="cu-dialog" @tap.stop>
					<view class="cu-list menu text-left solid-top">
						<!-- <view class="padding text-left"> -->
							<view class="padding-xl radius shadow-warp bg-white margin-top">
								<text class="text-red">致谢\n</text>
								<text>码农乐乐（我自己），\n录入数据的兆泉&莫桑，\n认真做ppt的宝们以及同组的所有其他成员。</text>
							</view>
						<!-- </view> -->
					</view>
				</view>
			</view>
			<view class="cu-item" :class="menuArrow?'arrow':''">
				<view class="content">
					<text class="cuIcon-tagfill text-red  margin-right-xs"></text>
					<text class="text-grey">标签</text>
				</view>
				<view class="action">
					<view class="cu-tag round bg-orange light">网络安全</view>
					<!-- <view class="cu-tag round bg-olive light">法律法规</view> -->
					<view class="cu-tag round bg-blue light">法律法规</view>
				</view>
			</view>
			<view class="cu-item" :class="menuArrow?'arrow':''">
				<view class="content">
					<text class="cuIcon-warn text-green"></text>
					<text class="text-grey">版本号</text>
				</view>
				<view class="action">
					<text class="text-grey text-sm">v0.0.1</text>
				</view>
			</view>
			<view class="cu-item" :class="menuArrow?'arrow':''">
				<button class="cu-btn content" open-type="contact">
					<text class="cuIcon-btn text-olive"></text>
					<text class="text-grey">一些想说</text>
				</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cuIconList: [{
					cuIcon: 'cardboardfill',
					color: 'red',
					badge: 120,
					name: 'VR'
				}, {
					cuIcon: 'recordfill',
					color: 'orange',
					badge: 1,
					name: '录像'
				}, {
					cuIcon: 'picfill',
					color: 'yellow',
					badge: 0,
					name: '图像'
				}, {
					cuIcon: 'noticefill',
					color: 'olive',
					badge: 22,
					name: '通知'
				}, {
					cuIcon: 'upstagefill',
					color: 'cyan',
					badge: 0,
					name: '排行榜'
				}, {
					cuIcon: 'clothesfill',
					color: 'blue',
					badge: 0,
					name: '皮肤'
				}, {
					cuIcon: 'discoverfill',
					color: 'purple',
					badge: 0,
					name: '发现'
				}, {
					cuIcon: 'questionfill',
					color: 'mauve',
					badge: 0,
					name: '帮助'
				}, {
					cuIcon: 'commandfill',
					color: 'purple',
					badge: 0,
					name: '问答'
				}, {
					cuIcon: 'brandfill',
					color: 'mauve',
					badge: 0,
					name: '版权'
				}],
				modalName: null,
				gridCol: 3,
				gridBorder: false,
				menuBorder: false,
				menuArrow: false,
				menuCard: true,
				skin: false,
				listTouchStart: 0,
				listTouchDirection: null,
			};
		},
		methods: {
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
			Gridchange(e) {
				this.gridCol = e.detail.value
			},
			Gridswitch(e) {
				this.gridBorder = e.detail.value
			},
			MenuBorder(e) {
				this.menuBorder = e.detail.value
			},
			MenuArrow(e) {
				this.menuArrow = e.detail.value
			},
			MenuCard(e) {
				this.menuCard = e.detail.value
			},
			SwitchSex(e) {
				this.skin = e.detail.value
			},

			// ListTouch触摸开始
			ListTouchStart(e) {
				this.listTouchStart = e.touches[0].pageX
			},

			// ListTouch计算方向
			ListTouchMove(e) {
				this.listTouchDirection = e.touches[0].pageX - this.listTouchStart > 0 ? 'right' : 'left'
			},

			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
			}
		}
	}
</script>

<style>
	.page {
		height: 100Vh;
		width: 100vw;
	}

	.page.show {
		overflow: hidden;
	}

	.switch-sex::after {
		content: "\e716";
	}

	.switch-sex::before {
		content: "\e7a9";
	}

	.switch-music::after {
		content: "\e66a";
	}

	.switch-music::before {
		content: "\e6db";
	}
	
	page{
		background-color: #55aaff;
	}
</style>
