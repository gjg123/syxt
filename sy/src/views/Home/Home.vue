<template>
	<div class="home">
		  <el-table
		    ref="multipleTable"
		    :data="tableData3"
		   border
		 
		    tooltip-effect="dark"
		    style="width: 100%"
		    @selection-change="handleSelectionChange">
		    
		
	          
		    
		    
		    <el-table-column
		      type="selection"
		      align="center"
		      width="55">
		    </el-table-column>
		    <el-table-column
		      label="商品条码"
		      align="center">
		      
		      <template slot-scope="scope">{{ scope.row.goodsBarCode }}</template>
		    </el-table-column>
		    
		     
		    <el-table-column
		      prop="goodsName"
		      label="商品名称"
		      align="center">
		      
		    </el-table-column>
		  
		    <el-table-column
		      prop="goodsPrice"
		      label="原价"
		      align="center"
		      show-overflow-tooltip>
		    </el-table-column>
		  
		  <el-table-column
		      prop="goodsDiscount"
		      label="折扣"
		      align="center"
		      show-overflow-tooltip>
		    </el-table-column>
		  
		  
		  <el-table-column
		      prop="goodsNum"
		      label="数量"
		      align="center"
		      show-overflow-tooltip>
		    </el-table-column>
		  
	  		<el-table-column
		      prop="newPrice"
		      label="现价"
		      align="center"
		      show-overflow-tooltip>
		    </el-table-column>
		    
		    <el-table-column
		      prop="total"
		      label="小计"
		      align="center"
		      show-overflow-tooltip>
		    </el-table-column>
	          
		  
		  </el-table>
		  <div class="footer">
		  	<div class="weibu">
		  	<div class="checkWrapper">
		  		<el-checkbox @change="isch" v-model="checked">共计{{checkNum}}件商品</el-checkbox>
		  		<span></span>
		  	</div>
		  	
		  	<div id="">
		  		
		  		<el-button @click="delet"  size="mini" type="danger">删除商品</el-button>
		  	</div>
		  </div>
		  <div class="bot">
		    <div class="inpWrapper">
		    	
		    	<div class="searchBox">
		    		<input type="text" placeholder="请输入关键字搜索产品" name="" id="" value="" class="search"/>
		    		<img src="../../assets/jp_03.png" class="imgjp" @click="centerDialogVisible = true"/>
		    	</div>
		    	<div class="syBox">
		    		<input type="text" placeholder="输入价格无码收银" name="" id="" value="" class="sy"/>
		    		<img src="../../assets/jp_03.png" class="syjp" @click="wumasy = true"/>
		    	</div>
		    
		    
		    </div>
		    <div class=" phoneBox">
		    	<div class="phoneWrapper">
		    		<input type="text" placeholder="请输入手机号" name="" id="" value="" class="phone"/>
		    		<img src="../../assets/jp_03.png" class="phoneImg" @click="shoujih = true"/>
		    	</div>
		    	<div class="user">
		    		<div class="username">
		    			<ul>
		    				<li>用户名</li>
		    				<li>1866666</li>
		    			</ul>
		    		</div>	
		    		<div class="yue">
		    			<ul>
		    				<li>余额</li>
		    				<li>100</li>
		    			</ul>
		    		</div>
		    		<div class="jifen">
		    			<ul>
		    				<li>积分</li>
		    				<li>20</li>
		    			</ul>
		    		</div>
		    	</div>
		    </div>
		    <div class="inpWrapper" @click="dialogs.show = true" >
		    	<div class="yinzi">
		    		收款3000元
		    	</div>
		    </div>
		  </div>
		  </div>
		  
		  
		  
		  
		<!--对话框  -->
		   <!--商品搜索弹框--> 
		 <el-dialog
		  title="商品搜索"
		  :visible.sync="centerDialogVisible"
		  width="30%"
		  center>
		
		    <el-form :model="form">
			    <el-form-item label="商品条码" :label-width="formLabelWidth">
			      <el-input v-model="form.tiaoma" autocomplete="off"></el-input>
			    </el-form-item>
			    <el-form-item label="商品名称" :label-width="formLabelWidth">
			     <el-input v-model="form.name" autocomplete="off"></el-input>
			    </el-form-item>
			  </el-form>
		  <span slot="footer" class="dialog-footer">
		    <el-button @click="centerDialogVisible = false">取 消</el-button>
		    <el-button type="primary" @click="centerDialogVisible = false">确 定</el-button>
		  </span>
		</el-dialog> 
		  
		  <!--无码收银弹框-->
		  <el-dialog
		  title="无码收银"
		  :visible.sync="wumasy"
		  width="30%"
		  center>
		
		    <el-form :model="formwumasy">
			    <el-form-item label="收款金额" :label-width="formLabelWidth">
			      <el-input v-model="formwumasy.price" autocomplete="off"></el-input>
			    </el-form-item>
			    
			  </el-form>
		  <span slot="footer" class="dialog-footer">
		    <el-button @click="wumasy = false">取 消</el-button>
		    <el-button type="primary" @click="wumasy = false">确 定</el-button>
		  </span>
		</el-dialog>
		  
		  
		 <!--无码收银手机号弹框--> 
		  <el-dialog
		  title="无码收银手机号"
		  :visible.sync="shoujih"
		  width="30%"
		  center>
		
		    <el-form :model="formwumasy">
			    <el-form-item label="手机号" :label-width="formLabelWidth">
			      <el-input v-model="isshoujih.price" autocomplete="off"></el-input>
			    </el-form-item>
			    
			  </el-form>
		  <span slot="footer" class="dialog-footer">
		    <el-button @click="shoujih = false">取 消</el-button>
		    <el-button type="primary" @click="shoujih = false">确 定</el-button>
		  </span>
		</el-dialog>
		
		<popup :shoukuan= 'shoukuan' :dialogs="dialogs"></popup>
		 <!--收款弹框--> 
		
		
		
	</div>
</template>

<script>
	
	import popup from '../../components/popup/popup.vue'
	export default {
		components:{
			popup
		},
		'id':'Home',
		 data() {
	      return {
	      	dialogs: {
		        show: false,
		        title: "",
		        sss: "8000"
		    },
	      	shoukuanK:{
	      		price:'200'
	      	},
	      	shoukuan:false,
	      	isshoujih:{
	      		price:'200'
	      	},
	      	formwumasy:{
	      		price:'200'
	      	},
  	        form: {
	          name: '商品名称',	  
	          tiaoma:'商品条码'
	        },
	       
	        shoujih:false,
	        wumasy: false,
	      	centerDialogVisible: false,
	      	formLabelWidth: '120px',
	      	checkNum:0,
	      	checked:'',
	      	checkArr:[],
	      	arr_null:[],
	        tableData3: [{
	          goodsBarCode: '商品条码',
	          goodsName: '商品名称',
	          goodsPrice:"原价",
	          goodsDiscount: '折扣',
	          goodsNum:10,
	          newPrice:20,
	          total:30
	        },
	        {
	          goodsBarCode: '商品条码',
	          goodsName: '商品名称',
	          goodsPrice:"原价",
	          goodsDiscount: '折扣',
	          goodsNum:10,
	          newPrice:20,
	          total:30
	        },{
	          goodsBarCode: '商品条码',
	          goodsName: '商品名称',
	          goodsPrice:"原价",
	          goodsDiscount: '折扣',
	          goodsNum:10,
	            newPrice:20,
	          total:30
	          
	        }
	        ],
	        multipleSelection: []
	      }
	    },
	
	    methods: {
	      toggleSelection(rows) {
	        if (rows) {
	          rows.forEach(row => {
	            this.$refs.multipleTable.toggleRowSelection(row);
	          });
	        } else {
	          this.$refs.multipleTable.clearSelection();
	        }
	        
	      },
	      isch(xxx){
	      	console.log(xxx)
	      },
	      handleSelectionChange(val) {
	        this.multipleSelection = val;
	        console.log(val)
	        this.checkArr = val
	    	this.checkNum = val.length
	        console.log(val.length)
	      },
	      delet(){
	      	console.log(this.checkArr)
	      	console.log(this.tableData3)	      	

	      },
	      searchK(){
	      	alert("123")
	      },
	      syK(){
	      	alert("4565")
	      },
	      phoneK(){
	      	alert("789")
	      }
       
	  
	    }
	}
</script>

<style scoped>
	.home{
		height:100%;
		background: #fff;
	}
	.weibu{
		height:30px;
		width:100%;
		background: #fff;
		border-bottom: 1px solid #ccc;
	}
	.weibu{
		height:50px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding:0 19px;
		box-sizing: border-box;
	}
	.bot{
		
		background: #fff;
		padding: 20px;
		width:100%;
		box-sizing: border-box;
		display: flex;
		justify-content: space-around;
		align-items: center;
	}
	.inpWrapper{
		padding: 0px;
		height:100px;
		width:30%;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	.search{
		margin-bottom: 20px;
		
		
	}
	.search,.sy{
		height:40px;
		width:100%;
		padding-left:10px;
		box-sizing: border-box;
		border:1px solid #000;
		
	}

	.yinzi{
		background: #0cec0d;
		width:100%;
		height:100%;
		color:#fff;
		display: flex;
		font-size: 30px;
		font-weight: bold;
		justify-content: center;
		align-items: center;
	}
	.searchBox,.syBox{
		width:100%;
		position: relative;
	}
	.imgjp,.syjp{
		position: absolute;
		top:5px;
		right:5px;
		width:35px;
		height:30px;
	}
	
	.phoneBox{
		padding: 0px;
		height:100px;
		width:30%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		border:1px solid #000;
	}
	.phoneWrapper{
		position: relative;
		height:50%;
		width:100%;
		box-sizing: border-box;
		border-bottom: 1px solid #000;
	}
	.phoneImg{
		position: absolute;
		top:10px;
		right:10px;
		width:35px;
		height:30px;
	}
	.user{
		width:100%;
		height:50%;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.phone{
		padding-left: 10px;
		box-sizing: border-box;
		width:100%;
		height:100%;
		border:none;
		outline: none;
	}
	.username,.yue,.jifen{
		width:33.33%;
		height:100%;
	}
	.username ul li,.yue ul li,.jifen ul li{
		height:25px;
		line-height: 25px;
		text-align: center;
	}
	.yue{
		border-left: 1px solid #000;
		border-right: 1px solid #000;
	}

</style>