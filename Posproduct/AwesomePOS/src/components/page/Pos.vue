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
                    <el-tabs >
                        <el-tab-pane label="汉堡" >
                            <div class="cookProducts">
                                <ul>
                                    <li v-for="products of cookProducts">
                                        <span><img :src="products.img_url"/></span>
                                        <span class="cookProducts-title">{{products.pname}}</span>
                                        <span class="cookProducts-price">￥{{(products.price).toFixed(2)}}元</span>
                                    </li>
                                </ul>
                            </div>
                        </el-tab-pane>
                        <el-tab-pane label="小吃">
                            <div class="cookProducts">
                                <ul>
                                    <li v-for="products of snackProducts">
                                        <span><img :src="products.img_url"/></span>
                                        <span class="cookProducts-title">{{products.pname}}</span>
                                        <span class="cookProducts-price">￥{{(products.price).toFixed(2)}}元</span>
                                    </li>
                                </ul>
                            </div>
                        </el-tab-pane>
                        <el-tab-pane label="饮料">
                            <div class="cookProducts">
                                <ul>
                                    <li v-for="products of drinkProducts">
                                        <span><img :src="products.img_url"/></span>
                                        <span class="cookProducts-title">{{products.pname}}</span>
                                        <span class="cookProducts-price">￥{{(products.price).toFixed(2)}}元</span>
                                    </li>
                                </ul>
                            </div>
                        </el-tab-pane>
                        <el-tab-pane label="套餐">
                            <div class="cookProducts">
                                <ul>
                                    <li v-for="products of mealProducts">
                                        <span><img :src="products.img_url"></span>
                                        <span class="cookProducts-title">{{products.pname}}</span>
                                        <span class="cookProducts-price">￥{{(products.price).toFixed(2)}}元</span>
                                    </li>
                                </ul>
                            </div>
                        </el-tab-pane>
                    </el-tabs>
                </div>
            </el-col>
        </el-row>
    </div>
</template>
<script>
    import axios from "axios";
    export default{
        data(){
            return{
                products:[
                    {product:"BBQ手撕猪肉堡",count:"2",price:22},
                    {product:"波纹薯条",count:"2",price:7},
                    {product:"香辣鸡腿堡",count:"1",price:25}
                ],
                oftenProducts:[],
                cookProducts:[],
                snackProducts:[],
                drinkProducts:[],
                mealProducts:[]
            } 
        },
        name:"pos",
        // created() {
        //     axios.get().then(res=>{

        //     }).catch(error=>{
        //         alert("网络错误,暂时不能访问")
        //     })
        // },
        mounted(){
            var orderHeight=document.body.clientHeight;
            document.getElementById("order-list").style.height=orderHeight+"px";
        },
        created() {
            var url="http://127.0.0.1:3000/oftenProducts";
            axios.get(url).then(res=>{
                this.oftenProducts=res.data;
            });
            var url="http://127.0.0.1:3000/productsList";
            axios.get(url).then(res=>{
                this.cookProducts=res.data[0];
                this.snackProducts=res.data[1]
                this.drinkProducts=res.data[2]
                this.mealProducts=res.data[3]
            })
        },
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

    .cookProducts>ul>li{
        list-style: none;
        border:1px solid #e5e9f2;
        width:23%;
        background-color:#fff;
        overflow: hidden;
        float: left;
        margin: 2px;
        padding: 2px;
        height:140px; 
    }
    
    .cookProducts>ul>li>span{
        float:left;
        display: block;
       
        
    }
    .cookProducts>ul>li>span>img{
       width:140px; 
       margin:2px;
    }
    .cookProducts-title{
        font-size: 18px;
        color:red;
        padding-left: 5px;
         padding-top:10px;
    }
    .cookProducts-price{
        font-size: 16px;
        padding-left:20px;
        padding-top:30px;
    }
    
</style>