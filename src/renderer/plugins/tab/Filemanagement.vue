<style lang='less' scoped>
	.filemanagement{
		height:700px;
		header{
			margin-bottom: 20px;
		}
	}
	.page_part{
		margin: 20px 0px;
		float: left;

	}
	.upload_area .ivu-input-group{
		width:100%;
		transition: all 0.5s ease 0s;
	}
	.donghua .ivu-input-group{
		width:25%;
	}
</style>
<template>
	<div class="filemanagement">
		<header>
			<Row>
				<Col span="6">
					<Dropdown style="margin-left: 20px">
						<Button type="primary">
							批量操作
							<Icon type="ios-arrow-down"></Icon>
						</Button>
						<DropdownMenu slot="list">
							<DropdownItem>下载</DropdownItem>
							<DropdownItem divided>删除</DropdownItem>
						</DropdownMenu>
					</Dropdown>
					<Button :size="buttonSize" type="primary">刷新</Button>
				</Col>
				<Col span="5">
					<Input search enter-button placeholder="输入object名称或ID" style="width: auto" on-change="donghua"/>
				</Col>
				<Col span="8" class="upload_area" :class="{'donghua':isUpload_area_donghua}">
					<Button :size="buttonSize" type="primary" @click="donghua" v-if="isUpload_area_donghua">上传文件</Button>
					<Input search enter-button="上传" placeholder="在此bucket上传文件..." on-change="donghua" v-else  />
				</Col>
			</Row>
		</header>
		<Content>
		    <Table :columns="columns" :data="tableData" height="620"></Table>
		    <div class="page_part">
		    	 <Page :total="400" show-elevator show-sizer />
		    </div>
		</Content>
	</div>
</template>
<script>
	import Vue from 'vue'
	export default {
		data(){
			return {
				isUpload_area_donghua:true,
				buttonSize:"default",
				tableData: [
                    {"fileName":"文件1","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件2","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件3","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件4","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"},
                    {"fileName":"文件5","fileSize":"145kb","sType":"归档存储","updateTime":"2018-09-07 11:05"}
                ],
                columns: [
                	{
                        type: 'selection',
                        width: 60,
                        align: 'center'
                    },
                    {key: 'fileName', title: '文件名',align: 'center'},
                    {key: 'fileSize', title: '文件大小',align: 'center'},
                    {key: 'sType', title: '存储类型',align: 'center'},
                    {key: 'updateTime', title: '更新时间',align: 'center'},
                    {key: 'operation', title: '操作',align: 'center',render: (h, params) => {
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: 'primary',
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
                                }, '下载'),
                                h('Button', {
                                    props: {
                                        type: 'error',
                                        size: 'small'
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
		},
		methods: {
			donghua(){
				console.log(31232)
				this.isUpload_area_donghua = !this.isUpload_area_donghua;
			}
		}

	}
</script>