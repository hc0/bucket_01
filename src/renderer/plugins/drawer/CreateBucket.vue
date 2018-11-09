<style lang='less' scoped>
	.drawer-footer{
		margin-left: 300px;
	}
	.vertical-center-modal{
        display: flex;
        align-items: center;
        justify-content: center;
        .ivu-modal{
            top: 0;
        }

    }
</style>
<template>
	<div>
		<Modal
	        title="创建存储仓库"
	        footer-hide
	        v-model="isShowCreateBucket.showorHide"
	        class-name="vertical-center-modal"
	    >
        	<Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="120">
        	    <FormItem label="Bucket 名称" prop="bucketname">
        	    	<Row>
        	    		<Col span="10">
        	        		<Input v-model="formValidate.bucketname" placeholder="请输入bucket名称"></Input>
        	    		</Col>
        	    	</Row>
        	    </FormItem>
        	    <FormItem label="区域" prop="area">
            		<Row>
            			<Col span="10">
            	    		<Select v-model="formValidate.area" placeholder="请输入存储区域">
            	    		    <Option value="华北">华北</Option>
            	    		    <Option value="华东">华东</Option>
            	    		    <Option value="华南">华南</Option>
            	    		    <Option value="香港">香港</Option>
            	    		    <Option value="亚太东南 (新加坡)">亚太东南 (新加坡)</Option>
            	    		    <Option value="亚太东南 (悉尼)">亚太东南 (悉尼)</Option>
            	    		    <Option value="亚太东北 (东京)">亚太东北 (东京)</Option>
            	    		    <Option value="美国西部 (硅谷)">美国西部 (硅谷)</Option>
            	    		    <Option value="欧洲中部 (法兰克福)">欧洲中部 (法兰克福)</Option>
            	    		    <Option value="美国东部 (弗吉尼亚)">美国东部 (弗吉尼亚)</Option>
            	    		    <Option value="亚太东南 (吉隆坡)">亚太东南 (吉隆坡)</Option>
            	    		    <Option value="亚太东南 (雅加达)">亚太东南 (雅加达)</Option>
            	    		    <Option value="英国（伦敦）">英国（伦敦）</Option>
            	    		    <Option value="亚太南部 (孟买)">亚太南部 (孟买)</Option>
            	    		</Select>
            			</Col>
            			<Col span="16">
            				<span>订购后不支持更换区域，请谨慎选择</span>
            			</Col>
            		</Row>
        	    </FormItem>
        	    <FormItem label="存储类型" prop="storageType">
        	    	<Row>
        	    		<Col span="16">
        	    			<RadioGroup v-model="formValidate.storageType" type="button">
        	    			    <Radio label="archive">归档存储</Radio>
        	    			</RadioGroup>
        	    		</Col>
        	    		<Col span="16">
        	    			<span>归档：数据长期存储、基本不访问。</span>
        	    		</Col>
        	    	</Row>
        	    </FormItem>
        	    <FormItem label="读写权限" prop="permission">
        	    	<Row>
        	    		<Col span="16">
        	    			<RadioGroup v-model="formValidate.permission" type="button">
        	    			    <Radio label="private">私有</Radio>
        	    			</RadioGroup>
        	    		</Col>
        	    	</Row>
        	    </FormItem>
        	    <FormItem label="标签" prop="tag">
        	        <Input v-model="formValidate.tag" type="textarea" :autosize="{minRows: 2,maxRows: 5}" placeholder="输出一个标签"></Input>
        	    </FormItem>
        	</Form>
            <div class="drawer-footer">
                <Button @click="isShowCreateBucket.showorHide = false">取消</Button>
                <Button @click="handleReset('formValidate')">重置</Button>
                <Button type="primary" @click="handleSubmit('formValidate')">提交</Button>
            </div>
	    </Modal>    
	</div>
</template>
<script>
	export default {
		props:["isShowCreateBucket"],
		data(){
			return{
				formValidate: {
                    bucketname: '',
                    area: '',
                    storageType:"",
                    permission:"",
                    tag: ''
                },
                ruleValidate: {
                    bucketname: [
                        { required: true, message: '不能为空', trigger: 'blur' },
                        {type: "string", required: true, pattern: /^[a-z0-9]+$/,message: '请输入英文和数字'},
                        {type: "string", required: true, pattern: /^\S{3,63}$/,message: '请输入 3-63 个字符'}
                    ],
                    area: [
                        { required: true, message: '请选择存储区域', trigger: 'change' }
                    ],
                    storageType: [
                        { required: true, message: '请选择存储类型', trigger: 'change' }
                    ],
                    permission: [
                        { required: true, message: '请选择权限类型', trigger: 'change' }
                    ],
                    tag:[
                    	{ required: true, message: '请输入一个标签', trigger: 'blur' },
                        { type: 'string', min: 2, max: 20, message: '请输入 2-20 个字符', trigger: 'blur' }
                    ]

                }
			}
		},
		methods: {
            handleSubmit (name) {
                this.$refs[name].validate((valid) => {
                    if (valid) {
                        this.$Message.success('验证成功,并已提交!');
                        this.isShowCreateBucket.showorHide = false;
                    } else {
                        this.$Message.error('验证失败!');
                    }
                })
            },
            handleReset (name) {
                this.$refs[name].resetFields();
            }
        }
	}
</script>

