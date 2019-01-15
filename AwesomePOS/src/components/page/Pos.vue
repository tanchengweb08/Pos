<template>
    <div class="pos">
        <el-row>
            <el-col :span="7" class="pos-roder" id="order-list">
                <el-tabs>
                    <el-tab-pane label="点餐">
                        <el-table :data="products" border style="width:100%" >
                            <el-table-column prop="product" label="商品名称"></el-table-column>
                            <el-table-column prop="count" label="商品数量" ></el-table-column>
                            <el-table-column prop="price" label="商品金额"></el-table-column>
                            <el-table-column  label="操作" fixed="right">
                                <template  slot-scope="scope">
                                    <el-button type="text" size="small">增加</el-button>
                                    <el-button type="text" size="small">删除</el-button>
                                </template>
                            </el-table-column>
                        </el-table>
                        <div class="order-btn">
                            <el-button type="warning">挂单</el-button>
                            <el-button type="danger">删除</el-button>
                            <el-button type="success">结账</el-button>
                        </div>
                    </el-tab-pane>
                    <el-tab-pane label="挂单">
                        挂单
                    </el-tab-pane>
                    <el-tab-pane label="外卖">
                        外卖
                    </el-tab-pane>
                </el-tabs>
            </el-col>
            <el-col>
                我是产品栏
            </el-col>
        </el-row>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                products:[
                    {product:"可乐",count:"2",price:"10"},
                    {product:"薯条",count:"2",price:"8"},
                    {product:"汉堡",count:"1",price:"25"}
                ]
            }
        },
        name:"pos",
        mounted(){
            var orderHeight=document.body.clientHeight;
            document.getElementById("order-list").style.height=orderHeight+"px";
        }
    }
</script>
<style scoped>
    .pos-roder{
        background-color:#F9FAFC;
        border-right:1px solid #C0CCDA;
        height:100%;
    }
    .order-btn{
        margin-top:10px;
    }
</style>