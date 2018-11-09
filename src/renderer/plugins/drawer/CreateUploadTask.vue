<style scoped lang="less">
	.state_upload{
		margin-bottom: 20px;
	}
</style>
<template>
	<div>
		<Drawer
		    title="上传任务"
		    v-model="isShowUploadTask.showorHide"
		    width="1000"
		    :mask-closable="false"
		    :styles="styles"
		>
	 	<div class="state_upload">
	 		<i>0</i> 已完成，<i>0</i> 失败，<i>5</i> 上传中，共 <i>5</i> 个文件
	 	</div>
	 	<div class="list_upload">		
    		<Table border :columns="columns" :data="tableData"></Table>
	 	</div>
		</Drawer>    
	</div>
</template>
<script>
	import Vue from 'vue';
	export default {
		props:["isShowUploadTask"],
		data(){
			return {
				styles: {
                    height: 'calc(100% - 55px)',
                    overflow: 'auto',
                    paddingBottom: '53px',
                    position: 'static'
                },
				tableData: [
                    {"name":"文件1","size":"123MB","bucketOrigin":"Bucket1","progress":30,"operation":"操作"},
                    {"name":"文件2","size":"123MB","bucketOrigin":"Bucket2","progress":70,"operation":"操作"},
                    {"name":"文件3","size":"123MB","bucketOrigin":"Bucket3","progress":64,"operation":"操作"},
                    {"name":"文件4","size":"123MB","bucketOrigin":"Bucket4","progress":30,"operation":"操作"},
                    {"name":"文件5","size":"123MB","bucketOrigin":"Bucket5","progress":90,"operation":"操作"}
                ],
                columns: [
                    {key: 'name', title:'文件名',align: 'center'},
                    {key: 'size', title: '文件大小',align: 'center',width:100},
                    {key: 'bucketOrigin', title: '目标 Bucket',align: 'center'},
                    {key: 'progress', title: '上传进度',align: 'center',width:300,render: (h, params) => {
            
                    	 return h('div', [
									h('Progress', {
	                                    props: {
	                                        percent: params.row.progress,
	                                        status: 'active'
	                                    },
	                                    style: {
	                                        marginRight: '5px'
	                                    },
	                                })
                    	 	]);
                    }},
                    {key: 'operation', title: '操作',align: 'center',width:80,render: (h, params) => {
                    	 return h('div', [
									h('Button', {
	                                    props: {
	                                        type: 'error',
	                                        size: 'small'
	                                    },
	                                    style: {
	                                        marginRight: '5px'
	                                    },
	                                    on: {
	                                        click: () => {
	                                            console.log(params.index)
	                                        }
	                                    }
	                                }, '删除')
                    	 	]);
                    }}
                ]
			}
		}
	}
</script>

	 		



	