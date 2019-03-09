<template>
	<div class="popup">
	 <el-dialog
		  title="订单收款"
		  :visible.sync="dialogs.show"
		  width="50%"
		  center>
		
		    <el-form :model="shoukuanK">
		    	<p class="z" style="text-align: center;width:100%;">总金额￥{{dialogs.sss}}</p>		    	
		    	<div class="aBox">
		    		<p class="" style="text-align: center;width:100%;">收款方式</p>
					<div class="tBox">
		    		<el-table
				    ref="multipleTable"
				    :data="tableData2"
				   border	
				   :show-header="false"
				    tooltip-effect="dark"
				    style="width: 100%"
				    @selection-change="handleSelectionChange">
		    

					    <el-table-column
					      label="现金"
					      align="center">
					      
					      <template slot-scope="scope">
					      	{{ scope.row.xianjin }}
					      </template>
					    </el-table-column>
					    
					     
					    <el-table-column
					     
					      align="center">
					      	<template slot-scope="scope">
						        <el-input class="inp" size="mini" v-model="input" placeholder="请输入内容"></el-input>
						        <el-button
						          size="mini"
						          type="danger"
						          @click="isshibai = true">收款</el-button>
						    </template>
					    </el-table-column>
					  </el-table>
					</div>
		    	</div>
		    	
		    	<div class="aBox">
		    		<el-table
					    ref="multipleTable"
					    :data="tableData5"
					   border
					 
					    tooltip-effect="dark"
					    style="width: 100%"
					    @selection-change="handleSelectionChange">
					    
					
				          
					    
					    
					    <el-table-column
					      type="selection"
					      label="全选"
					     
					      align="center"
					      width="55">
					     
      
					    </el-table-column>
					    <el-table-column
					      label="收款方式"
					      align="center">
					      
					      <template slot-scope="scope">{{ scope.row.goodsBarCode }}</template>
					    </el-table-column>
					    
					     
					    
					  
					    <el-table-column
					      prop="goodsPrice"
					      label="收款金额"
					      align="center"
					      show-overflow-tooltip>
					    </el-table-column>
					  
					  <el-table-column
					      prop="goodsDiscount"
					      label="状态"
					      align="center"
					      show-overflow-tooltip>
					    </el-table-column>
					  
					  
					  <el-table-column
					      prop="goodsNum"
					      label="时间"
					      align="center"
					      show-overflow-tooltip>
					   </el-table-column>
					  </el-table>
					  <div class="weibu">
					  	<div class="checkWrapper">
					  		
					  		<span>总金额00</span>
					  	</div>
					  	
					  	<div id="">
					  		
					  		<el-button  size="mini" type="danger">退款</el-button>
					  	</div>
					  	
					  </div>
					  
					    
		    	</div>
			  </el-form>	
			  <span slot="footer" class="dialog-footer">
				    <el-button @click="dialogs.show = false">取 消</el-button>
				    <el-button type="primary" @click="dialogs.show = false">确 定</el-button>
			  </span>
		</el-dialog>
		
		
		
		
		<el-dialog
		  title="订单收款"
		  :visible.sync="isshibai"
		  width="30%"
		  center>
		
		    <el-form :model="shibaidata">		    	
		    	<p class="ce">总金额￥3000</p>
		    	
		    	<div class="ce">
		    		<img src="../../assets/2.png" style="width:80px;height:80px;"/>
		    	</div>
		    	<p class="ce">所有已收款项原路退还</p>
			  </el-form>
		  <span slot="footer" class="dialog-footer">
		    
		    <el-button type="primary" @click="isshibai = false">确 定</el-button>
		  </span>
		</el-dialog>
	</div>
</template>

<script>
	export default {
		data(){
			return {
				isshibai:false,
				input:'输入内容',
				multipleSelection: [],
				shibaidata:{
					issb:"谁败了"
				},
				tableData5: [{
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
				tableData2:[
					{
						xianjin:'现金',
						bu:'111'
					},
					{
						xianjin:'拉卡拉',
						bu:'111'
					},
					{
						xianjin:'pos',
						bu:'222'
					}
				]
			}
		},
		props:{
			shoukuanK:Object,
			
	      	dialogs: Object,
		},
		methods:{
			sk(){
				this.isshibai=true
			},
			checkboxT(row,index){
				console.log(row,index)
			},
			handleSelectionChange(val) {
		        this.multipleSelection = val;
		        
		        console.log(val.length)
	      },
		}
		
	}
</script>

<style>
	.weibu{
		height:50px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding:0 19px;
		box-sizing: border-box;
	}
	.aBox{
		padding: 0 30px;
	}
	.inp{
		display: inline-block;
		width:10px;
	}
	.popup .el-dialog__header{
		padding: 5px 10px !important;
	}
	.popup .el-dialog__body{
		padding: 5px 10px !important;
	}
	.popup .el-dialog--center .el-dialog__body{
		padding: 5px 0px !important;
	}
	.z{
		border-bottom: 1px solid #000;
	}
	.tBox .el-input {
	    position: relative;
	    font-size: 14px;
	    display: inline-block;
	    width: 60%;
	    margin-right:20px;
	}
	.ce{
		width:100%;
		text-align: center;
	}
</style>