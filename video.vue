<template>
	<div class='video'>
		<div class='video_h'>
			<img :src="video.src" alt="">
			<span class='video_h_One' v-if="video.type==1">{{ video.time }}</span>
			<span class='video_h_Two' v-if="video.type==2">{{video.now}}</span>
		</div>	
		<div class='video_f'>
			<p>{{video.title}}</p>
			<div class='video_f_One' v-if="video.type==1">
				<span><i></i>{{video.playTimes}}</span>
				<span><i></i>{{video.commentTimes}}</span>
			</div>
			<div class='video_f_Two' v-if="video.type==2">
				<p>{{video.detail}}</p>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	props:['video']
}	
</script>
<style scoped lang='less'>
.i_icon2(@left:0;@top:0){
		display:inline-block;
		width:.12rem;
		height:.12rem;
		background: url(../assets/yk.png) no-repeat;
		background-size: 3rem 3rem;
		background-position:@left @top;
		margin:0 auto;
	}
	.video{
		display:inline-block;
		font-size:.14rem;
		width:44%;
		margin:4% 3%;
		background:#f5f5f5;
		.video_h{
			display:inline-block;
			position:relative;
			.video_h_One{
				position:absolute;
				bottom:5px;
				right:5px;
				color:#ddd;
			}
			.video_h_Two{
				position:absolute;
				bottom:5px;
				left:5px;
				color:#ddd;
				font-size:0.12rem;

			}
			img{
				width:100%;
				vertical-align:bottom;
			}
		}
		.video_f{
			padding:.05rem;
			p{
				overflow:hidden;
				white-space:nowrap;
				text-overflow:ellipsis;
			}
			.video_f_One{
				span{
				color:#909090;
				}
				span:nth-child(1){
					i{
						.i_icon2(-.3rem);
						margin-right:5px;
					}
				}
				span:nth-child(2){
					i{
					.i_icon2(-.6rem);
					margin-right:5px;
					}
				}
			}
			.video_f_Two{
				p{
					overflow:hidden;
					white-space:nowrap;
					text-overflow:ellipsis;
					color:#909090;
					font-size:0.12rem;
				}
			}
			
		}
	}
</style>