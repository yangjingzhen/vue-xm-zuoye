<template>
	<div>
		<h2>首页</h2>
		<div class="top5Con">
			<h2>本周最受欢迎TOP5</h2>
			<ul class="top5list">
				<li v-for="(item,index) in top5Arr">
					<router-link :to="'/item/'+item.pro_id">
						<div class="top5_img"><img :src="item.pro_img[0].url" /></div>
						<div class="top5_text">
							<div>{{item.pro_name}}</div>
							<div>{{item.pro_Joiner}}人已参加</div>
						</div>
					</router-link>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	export default {
		name:'Mymain',
		data:function(){
			return {
				top5Arr:[]
			}
		},
		mounted:function(){
			axios.post("https://www.jvhv.com/siteindex.php/Index/Index.html").then((res)=>{
				this.top5Arr=res.data.data.CourseTop5;
			})
		}
	}
</script>

<style>
	
</style>