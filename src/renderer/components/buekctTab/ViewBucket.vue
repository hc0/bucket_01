<style lang='less' scoped>
	.viewBucket{
		position: relative;
		top:0px;
		width:100%;
		box-sizing: border-box;
		header{
			width:100%;
			height: 50px;
			line-height: 50px;
			background: #ebecec;
			box-sizing: border-box;
			box-shadow: inset 0px 0px 1px #555;
			padding-left:20px;
			h3{
				font-size: 20px;
				font-weight: bold;
				float: left;
			}
			.r_p{
				float: right;
				.f_s{
					    font-weight: 400;
    					color: #9b9ea0;
    					&+span{
    						color: #373d41;
    						margin-right:20px;
    					}
				}
			}
		}
		.ivu-layout-content{
			padding:20px;
			background: url('../../../../static/images/bg1.png') no-repeat;
			background-position:center center;
			background-size:80% auto;
			// filter: blur(0px) grayscale(0.7) hue-rotate(110deg);
		}
	}
</style>
<template>
	<div class="viewBucket">
		<header>
			<h3>{{getbucketname}}</h3>
			<div class="r_p">
				<span class="f_s">读写权限：</span><span>私有</span>
				<span class="f_s">类型：</span><span>归档</span>
				<span class="f_s">存储区域：</span><span>华北</span>
				<span class="f_s">创建时间：</span><span>2018-09-07 09:17</span>
			</div>
		</header>
		<Content>
			<Tabs value="name1">
		        <TabPane label="文件管理" name="name1">
		        	<Filemanagement></Filemanagement>
		        </TabPane>
		        <TabPane label="概览" name="name2">概览</TabPane>
		    </Tabs>
		</Content>
	</div>
</template>
<script>
	import Filemanagement from "../../plugins/tab/Filemanagement.vue";
	export default {
		data(){
			return {

			}
		},
		computed:{
			getbucketname(){
				return this.$store.state.Buckets.bucketinfo.bucketname;
			}
		},
		components:{
			Filemanagement
		}
	}
</script>