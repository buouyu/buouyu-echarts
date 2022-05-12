<template>
	<view class="content">
		<img src="static/logo.png"></img>
		<buouyuEcharts  :option="option" ref="buouyu" canvasId="buouyu" />
	</view>
</template>

<script>
	import buouyuEcharts from 'components/buouyu-echarts'
	export default {
		components: {
			buouyuEcharts
		},
		data() {
			return {
				option: null
			}
		},
		onLoad() {

		},
		mounted() {
			this.initBuouyuEcharts()
		},
		methods: {
			getRandom(min, max) {
				return Math.floor(Math.random() * (max - min)) + min
			},
			initBuouyuEcharts() {
				const option = {
					xAxis: {
						type: 'category',
						data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
					},
					yAxis: {
						type: 'value',
						min: 0,
						max: 1000,
						axisLabel: {
							margin: 3,
						}
					},
					series: [{
						data: [300, 400, 800, 900, 700, 774, 400],
						type: 'line',
						smooth: true,
					}],
					visualMap: {
						min: 0,
						max: 1300,
						calculable: false,
						show: false,
						realtime: false,
						inRange: {
							color: ["#313695", "#4575b4", "#74add1", "#abd9e9", "#e0f3f8", "#ffffbf", "#fee090",
								"#fdae61",
								"#f46d43", "#d73027", "#a50026"
							]
						}
					}
				}
				this.option = option //绑定数据组件就会初始化渲染
				const data = [300, 400, 800, 950, 700, 774, 400]
				const buouyuCharts = this.$refs.buouyu
				setInterval(() => {
					data.push(this.getRandom(0, 1000))
					data.shift()
					buouyuCharts.setOption({
						series: [{
							data,
						}]
					})
				}, 1000)
			},
		}
	}
</script>



<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
	}



	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
