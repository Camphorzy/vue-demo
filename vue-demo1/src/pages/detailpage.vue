<template>
    <div class="detail-wrap">
        <div class="detail-left">
            <div class="product-board">
                <img :src="productIcon">
                <ul>
                    <router-link tag='li'  v-for='(item,index) in product' :key='index' :to='{path: item.path}' active-class="active">{{item.name}}</router-link>
                </ul>
            </div>
        </div>
        <div class="detail-right">
            <keep-alive>
                <router-view></router-view>
            </keep-alive>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            product:[
                {
                    name:'数据统计',
                    path:'count',
                    icon: require('../assets/1.jpg'),
                    active:false
                },
                {
                    name:'数据预测',
                    path:'forecast',
                    active:false
                },
                {
                    name:'流量分析',
                    path:'analysis',
                    active:false
                },
                {
                    name:'广告发布',
                    path:'publish',
                    active:false
                },
            ],
            imgMap:
                {'/detail/count':require('../assets/1.jpg'),
                '/detail/forecast':require('../assets/2.jpg'),
                '/detail/analysis':require('../assets/3.jpg'),
                '/detail/publish':require('../assets/4.jpg')}
            
        }
    },
    computed:{
        productIcon () {
            // console.log(this.$route.path,this.imgMap)
            return this.imgMap[this.$route.path];
        }
    }

}
</script>

<style>
.detail-wrap{
    width: 1200px;
    margin: 0 auto;
    overflow: hidden;
}
.detail-left{
    float: left;
    width: 200px;
    text-align: center
}
.detail-right{
    float: left;
    width: 980px;
    margin-left:20px;
}
.product-board{
    background: #fff;
    padding: 20px 0;
}
.product-board ul{
    margin-top: 20px;
}
.product-board li{
    text-align: left;
    padding: 10px 15px;
    cursor: pointer;
}
.product-board li :active,.product-board li:hover{
    background: #4fc08d;
    color:#fff;
}
.product-board li a{
    display: block;
}  
.sales-board{
    background: #fff;
}
.sales-board-intro h2{
    font-size: 20px;
    padding:20px;
}
.sales-board-intro p{
    background: #f7fcff;
    padding: 10px 20px;
    color: #999;
    line-height: 1.8;
}
.sales-board-form{
    padding: 30px 20px;
    font-size: 14px;
}
.sales-board-line{
    clear: both;
    padding-bottom: 20px;
}
.sales-board-line-left{
    display: inline-block;
    font-size: 13px;
}
.sales-board-line-right{
    display: inline-block;
    width: 75%;
    font-size: 13px;
}
.sales-board-des{
    border-top:20px solid #f0f2f5;
    padding: 15px 20px;
}
.sales-board-des p{
    line-height: 1.6;
}
.sales-board-des h2{
    font-size: 20px;
    padding-bottom: 15px;
}
.sales-board-des h3{
    font-size: 18px;
    font-weight: bold;
    padding:20px 0 10px 0;
}
.sales-board-des li{
    padding: 5px 0;
}
.sales-board-table{
    width: 100%;
}
.sales-board-table th{
    background: #4fc08d;
    color: #fff;
}
.sales-board-table td{
    border: 1px solid #f0f2f5;
    padding: 15px;
}
</style>
