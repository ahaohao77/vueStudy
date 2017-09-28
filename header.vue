<template>
	<div class='header'>
		<div class="header_l">
			<router-link :to="{ name:'test'}">
				<img src="../assets/yklogo.png" alt="">
			</router-link>
			<span @click="pdClick1=!pdClick1,pdClick2=false" :class="{ on: pdClick1 }"><i></i>频道</span>
		</div>
		<div class="header_r">

			<span @click="pdClick2=!pdClick2,pdClick1=false,gotest()" :class="{ on: pdClick2 }"><i></i>搜索</span>
			<router-link to="/Hello" tag='span'>
				<i></i>登录
			</router-link>
		</div>
	</div>
</template>
<script>
export default{
	data () {
		return{
			pdClick1:false,
			pdClick2:false
		}
	},
	methods:{
		gotest(){
			this.$router.push('/')
			// this.$router.replace({name : 'test'})  替换地址
			// this.$router.go(-3) 前进3页。后退3页
		}
	}
}
</script>
<style scoped lang='less'>
/*scoped让当前页面的样式只作用于当前*/
	.flex(@just:space-between;@align:center){
		display:flex;
		justify-content:@just;
		align-items:@align;
	}
	.i_coin(@left:0;@top:0){
		display:block;
		width:.16rem;
		height:.16rem;
		background: url(../assets/mheader.png) no-repeat;
		background-size: 0.96rem 1.44rem;
		background-position:@left @top;
		margin:0 auto;
	}
	.header{
		.flex();
		padding:.1rem;
		font-size:.12rem;
		.header_l{
			.flex();
			img{
				width:1.2rem;
			}
			span{
				display:inline-block;
				margin-left: .1rem;
				i{
					.i_coin();
				}
				&.on{
					color:#06a7e1;
					i{
						background-position:-.48rem 0;
					}
				}
			}
		} 
		.header_r{
			span{
				display:inline-block;
			}
			span:nth-child(1){
				margin-right:.1rem;
				i{
					.i_coin(-.24rem);
				}
				&.on{
					color:#06a7e1;
					i{
						background-position:-.72rem 0;
					}
				}
			}
			span:nth-child(2){
				i{
					.i_coin(0;-0.24rem);
				}				
			}
		}
	}
</style>