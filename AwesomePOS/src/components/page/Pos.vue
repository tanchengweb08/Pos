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
            <el-col :span="17">
                <div class="often-product">
                    <div class="often-product-title">常用商品</div>
                    <div class="often-product-list">
                        <ul>
                            <li v-for="product of oftenProducts">
                                <span>{{product.product}}</span>
                                <span class="often-product-price">￥{{(product.price).toFixed(2)}}元</span>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="products-type">
                    <el-tabs>
                        <el-tab-pane label="汉堡">
                            汉堡
                        </el-tab-pane>
                        <el-tab-pane label="小吃">
                            小吃
                        </el-tab-pane>
                        <el-tab-pane label="饮料">
                            饮料
                        </el-tab-pane>
                        <el-tab-pane label="套餐">
                            套餐
                        </el-tab-pane>
                    </el-tabs>
                </div>
            </el-col>
        </el-row>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                products:[
                    {product:"可口可乐",count:"2",price:"10"},
                    {product:"薯条",count:"2",price:"8"},
                    {product:"香辣鸡腿堡",count:"1",price:"25"}
                ],
                oftenProducts:[
                    {id:1,product:"可口可乐",price:"10"},
                    {id:2,product:"薯条",price:"8"},
                    {id:3,product:"香辣鸡腿堡",price:"25"},
                    {id:4,product:"甜筒",price:"5"},
                    {id:5,product:"麻薯",price:"8"},
                    {id:6,product:"新奥尔良烤翅",price:"8"},
                    {id:7,product:"炸鸡腿",price:"10"},
                    {id:8,product:"蓝山咖啡",price:"25"},
                    {id:9,product:"全家桶",price:"98"},

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
    .often-product-title{
        height:20px;
        border-bottom: 1px solid #d3dce6;
        background-color: #f9fafc;
        padding: 10px;
        text-align: left;
    }
    .often-product-list ul li{
        list-style: none;
        float: left;
        border:1px solid #e5e9f2;
        padding: 10px;
        margin: 10px;
        background-color:#fff;
    }
    .products-type{
        clear:both;
    }
</style>