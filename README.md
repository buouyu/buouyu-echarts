# buouyu-echarts-demo
# 高兼容性echarts组件buouyu-echarts，支持APP,小程序，H5的echarts uni-app组件
<a name="LnTeA"></a>
# 介绍
众所周知uni-app是一套代码可以应用多个平台的移动端前端框架
用起来确实爽，小编也爱不释手
但需要做一些复杂的图标时，引入echarts，却失去了uni-app最牛逼的特性
看一下官方提供的
当然也有其他方式引入echarts，但是都不能做到app,小程序，h5都支持的
![image.png](https://cdn.nlark.com/yuque/0/2022/png/12993992/1652361941320-14788397-43c0-4082-aedc-a8e14025d4c3.png#clientId=u50307c11-5eea-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=886&id=ue94377ad&margin=%5Bobject%20Object%5D&name=image.png&originHeight=886&originWidth=971&originalType=binary&ratio=1&rotation=0&showTitle=false&size=86685&status=done&style=none&taskId=u10cf22fe-6462-434d-b0c2-ff60ea620bb&title=&width=971)
这还用个吊毛呀，不知道你们有没有遇到跟我一样的问题
小编研究数日，总结了一套方案，只为解决一个问题：
**把以上所有的叉叉变成勾勾**
本着共享开源的原则，小编已经把源码分享到GitHub，欢迎各位大佬们添花
github demo地址：[https://github.com/1879153421/buouyu-echarts](https://github.com/1879153421/buouyu-echarts)
当然也有很多不足之处，也请大佬们多多指教，小编闲暇之余会不断更新的
<a name="Aq7i4"></a>
# 快速入门
<a name="pbmjX"></a>
## 1、npm 直接安装
直接通过npm安装即可
npm 模块地址：[https://www.npmjs.com/package/buouyu-echarts](https://www.npmjs.com/package/buouyu-echarts)
```bash
npm i buouyu-echarts
```
若项目根目录下没有package.json 文件，可以先执行 npm init
安装失败可能的原因：
     大部分开发者可能都设置了淘宝镜像源，这里需要设置成原来的地址
```javascript
// 查询当前配置的镜像 npm get registry //https://registry.npmjs.org/ 
// 设置成淘宝镜像 npm config set registry http://registry.npm.taobao.org/ 
// 换成原来的 npm config set registry https://registry.npmjs.org/
```
也有可能之前的版本不见了，可以把package.json总的buouyu-echarts删掉，在执行npm i buouyu-echarts安装最新的
安装成功以后直接在需要用的页面引入
```javascript
import buouyuEcharts from 'buouyu-echarts'
```
components挂在一下
```javascript
components: {
			buouyuEcharts
		},
```
配置option
```javascript
data() {
			return {
				option: {
					xAxis: {
						type: 'category',
						data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
					},
					yAxis: {
						type: 'value',
					},
					series: [{
						data: [820, 932, 901, 934, 1290, 774, 660],
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
							color: ["#313695", "#4575b4", "#74add1", "#abd9e9", "#e0f3f8", "#ffffbf", "#fee090", "#fdae61",
								"#f46d43", "#d73027", "#a50026"
							]
						}
					}
				},
			}
		},
```
引入DOM结构
```html
<buouyuEcharts :option="option" canvasId="buouyu" />
```
这样就你能在app，小程序，h5都能看到同样的效果啦
![image.png](https://cdn.nlark.com/yuque/0/2022/png/12993992/1652363719918-85b1c9aa-f6a0-4154-aca0-ef9d2ee6659c.png#clientId=u50307c11-5eea-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=200&id=u6214f3d1&margin=%5Bobject%20Object%5D&name=image.png&originHeight=200&originWidth=380&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9813&status=done&style=none&taskId=uf692c54d-66e2-443b-b47b-41944c99115&title=&width=380)
当然也可以全局挂在
在根目录的main.js
```javascript
import Vue from 'vue'
import App from './App'
import buouyuEcharts from 'buouyu-echarts' //引入buouyu-echarts
 Vue.component('buouyuEcharts',buouyuEcharts)  //挂在到全局
Vue.config.productionTip = false
App.mpType = 'app'
const app = new Vue({
    ...App
})
app.$mount()
```
然后就可以在任意页面直接用啦
```html
<buouyuEcharts :option="option" canvasId="buouyu" />
```
跟以上类似，效果一样

<a name="StoNt"></a>
## 2、直接下载引入
github项目地址:[https://github.com/1879153421/buouyu-echarts](https://github.com/1879153421/buouyu-echarts)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/12993992/1652371683799-6a530971-5f63-48ac-be52-5f50cd075aa7.png#clientId=uf49d8218-17c0-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=444&id=ub5574dd7&margin=%5Bobject%20Object%5D&name=image.png&originHeight=444&originWidth=923&originalType=binary&ratio=1&rotation=0&showTitle=false&size=40392&status=done&style=none&taskId=ua6af82a4-184b-4f43-b3e9-5f96c646e3f&title=&width=923)
由于本组件依赖echarts，所以要安装echarts
```bash
npm i echarts
```
然后就可以直接在项目中使用buouyu-echarts啦
使用操作跟上面类似
<a name="CKeAW"></a>
# 教程
<a name="w5uqd"></a>
## 基础配置option
参考echarts官网：[https://echarts.apache.org/zh/index.html](https://echarts.apache.org/zh/index.html)
<a name="C5WO5"></a>
## 设置宽高
```html
<buouyuEcharts height="12rem" width="80%" :option="option"  canvasId="buouyu" />
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/12993992/1652369096883-45b0d2e1-540e-4587-9479-7d7ad5134b42.png#clientId=uf49d8218-17c0-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=272&id=u84db1e07&margin=%5Bobject%20Object%5D&name=image.png&originHeight=272&originWidth=475&originalType=binary&ratio=1&rotation=0&showTitle=false&size=11620&status=done&style=none&taskId=u184bb59a-4f01-4bec-b1dd-f3134cdf269&title=&width=475)
<a name="V8jI4"></a>
## 动态渲染数据
添加个ref
```html
<buouyuEcharts  :option="option" ref="buouyu" canvasId="buouyu" />
```
```javascript
data() {
			return {
				option: null
			}
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
				const buouyuCharts = this.$refs.buouyu //里面有个setOption方法
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
```
效果
![pilla1r.gif](https://cdn.nlark.com/yuque/0/2022/gif/12993992/1652369749371-27159347-5615-4f83-89c5-3628baebd64e.gif#clientId=uf49d8218-17c0-4&crop=0.0181&crop=0&crop=1&crop=1&from=drop&height=192&id=u996d2226&margin=%5Bobject%20Object%5D&name=pilla1r.gif&originHeight=196&originWidth=387&originalType=binary&ratio=1&rotation=0&showTitle=false&size=106550&status=done&style=none&taskId=u6967e125-d1ef-46b0-998b-9e76031d092&title=&width=380)
<a name="MfSyx"></a>
## 所有属性
| **参数** | **说明** | 是否必填 | **类型** | **传参示例** | **默认值** |
| --- | --- | --- | --- | --- | --- |
| canvasId | 唯一标识，同一组件里不要设置相同的值 | 是 | string | buouyu | ——— |
| option | 参考echarts官网配置 | 是 | object | ——— | ——— |
| width | 宽度，支持px,rem,rpx,vw等 | 否 | string | 90%，30rem | 100% |
| height | 宽度，支持px,rem,rpx,vh等 | 否 | string | 300px,30vh | 500rpx |

有兴趣的可以一起学习交流
小编微信：buouyupro
