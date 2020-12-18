<template>
	<view>

		<index-tabbar :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap">
		</index-tabbar>

		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newslist" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(index)">
						<template v-if="items.list.length>0">
							<block v-for="(item,index1) in items.list" :key="index1">
								<index-list :item="item" :index="index1" @handleListItem="handleListItem(arguments)"></index-list>
							</block>
							<!-- 上拉加载 -->
							<load-more :loadtext="newslist[index].loadtext"></load-more>
						</template>
						<template v-else>
							<!-- 无内容默认 -->
							<view class="nothing u-f-ajc">
								<image src="../../static/common/nothing.png" mode="widthFix"></image>
							</view>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>

	</view>
</template>


<script>
	import indexList from "../../components/index/index-list.vue";
	import indexTabbar from "../../components/index/index-tabbar.vue";
	import loadMore from "../../components/common/load-more.vue";
	export default {
		components: {
			indexList,
			indexTabbar,
			loadMore
		},
		data() {
			return {
				swiperheight: 500,
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "推荐",
						id: "tuijian"
					},
					{
						name: "体育",
						id: "tiyu"
					},
					{
						name: "热点",
						id: "redian"
					},
					{
						name: "财经",
						id: "caijing"
					},
					{
						name: "娱乐",
						id: "yule"
					},
				],
				newslist: [{
						loadtext: "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
						loadtext: "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
						loadtext: "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
						loadtext: "上拉加载更多",
						list: []
					},
					{
						loadtext: "上拉加载更多",
						list: []
					},
					{
						loadtext: "上拉加载更多",
						list: []
					}
				],


			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100)
					this.swiperheight = height;
				}
			});
		},
		methods: {
			loadmore(index) {
				if (this.newslist[index].loadtext != "上拉加载更多") {
					return
				}
				this.newslist[index].loadtext = "加载中"
				setTimeout(() => {
					let obj = {
						userpic: "../../static/demo/userpic/12.jpg",
						username: "昵称",
						isguanzhu: true,
						title: "我是标题",
						type: "video", // img:图文,video:视频
						titlepic: "../../static/demo/datapic/11.jpg",
						playnum: "20w",
						long: "2:47",
						infonum: {
							index: 1, //0:没有操作，1:顶,2:踩；
							dingnum: 11,
							cainum: 11,
						},
						commentnum: 10,
						sharenum: 10,
					}
					this.newslist[index].list.push(obj)
					this.newslist[index].loadtext = "上拉加载更多"
				}, 1000);
				// this.newslist[index].loadtext = "没有更多数据"
			},
			// tabbar点击事件
			tabtap(index) {
				this.tabIndex = index;
			},
			// 滑动事件
			tabChange(e) {
				this.tabIndex = e.detail.current;
			},
			//点击关注
			handleListItem(e) {
				// let obj = this.newslist[this.tabIndex].list[e[1]]
				this.newslist[this.tabIndex].list[e[1]] = Object.assign(this.newslist[this.tabIndex].list[e[1]], e[0])
			},
		},
	}
</script>

<style lang="scss">
	.nothing {
		background-color: #FFFFFF;
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;

		image {
			width: 50%;
		}
	}
</style>
