<template>
	<div class="home_m">
		 <main class="m_product">
                <section class="product_box">
                    <!-- <div class="product_top">
                        <a href="#" class="product_left">
                            <img src="../assets/images/jd_skill.png" alt="" class="miaosha_icon">
                            <strong class="dianshu">六点场</strong>
                            <span class="time">00:21:43</span>
                        </a>
                    </div> -->
                    <div class="share_title">
                                <p class="share_text">现货热卖</p>
                            </div>
                    <div class="product_content">
                        <ul>
                        
                            <li class="product_skill_item" v-for="(item,index) in homeDatas" :key="index">
                                <router-link :to="'/detail/'+item.product_id" class="product_skill_item_link">
                                    <img v-lazy="item.product_img_url" alt="" class="product_skill_item_cion lazy-img-fadein">
                                    <p class="nowprice">
                                        <i style="text-decoration: none;font-style: normal;font-size: 12px">¥</i>
                                        <span class="now_price">{{item.product_price}}</span>
                                    </p>
                                    <p class="oldprice">
                                        <i style="text-decoration: none;font-style: normal;font-size: 12px">¥</i>
                                        <del class="old_price">{{item.product_uprice}}</del>
                                    </p>
                                </router-link>
                            </li>
                        
                        </ul>
                    </div>
                </section>
                <div class="left_share_quality_content clearfix">
                    <div class="share_quality">
                        <div class="share_quality_top">
                            <div class="share_title">
                                <p class="share_text">为你推荐</p>
                            </div>
                        </div>
                        <div class="share_quality_left not_eng_box">
                            <ul>
                                <li class="not_eng_item" v-for="(item, index) in mainDatas" :key=index>
                                    <router-link  class="not_eng_link" :to="'/detail/'+item.product_id">
                                        <img v-lazy="item.product_img_url" alt="" class="not_eng_pic lazy-img-fadein">
                                        <div class="not_eng_info">
                                            <p class="not_eng_title">{{item.product_name}}</p>
                                            <p class="not_eng_text">
                                                <i style="text-decoration: none;font-style: normal;font-size: 12px">¥</i>
                                                <span class="more_info_price_txt">{{item.product_price}}</span>
                                            </p>
                                        </div>
                                    </router-link>
                                </li>
                        
                            </ul>
                        </div>
                    </div>
                </div>
            </main>
	</div>
</template>
<script>
    export default{
        data(){
            return {
                homeDatas : [],
                mainDatas:[{"product_id":1,"product_img_url":"https://img10.360buyimg.com/n2/jfs/t1/64731/3/9170/340030/5dc14d57E1ca5a78e/75ab15c91efd5d4d.jpg", "product_name":"法国兰蔻", "product_price":20},
                {"product_id":1,"product_img_url":"https://img10.360buyimg.com/n2/jfs/t1/64731/3/9170/340030/5dc14d57E1ca5a78e/75ab15c91efd5d4d.jpg", "product_name":"法国兰蔻", "product_price":20},
                {"product_id":1,"product_img_url":"https://img10.360buyimg.com/n2/jfs/t1/64731/3/9170/340030/5dc14d57E1ca5a78e/75ab15c91efd5d4d.jpg", "product_name":"法国兰蔻", "product_price":20},
                {"product_id":1,"product_img_url":"https://img10.360buyimg.com/n2/jfs/t1/64731/3/9170/340030/5dc14d57E1ca5a78e/75ab15c91efd5d4d.jpg", "product_name":"法国兰蔻", "product_price":20},
                {"product_id":1,"product_img_url":"https://img10.360buyimg.com/n2/jfs/t1/64731/3/9170/340030/5dc14d57E1ca5a78e/75ab15c91efd5d4d.jpg", "product_name":"法国兰蔻", "product_price":20},
                {"product_id":1,"product_img_url":"https://img10.360buyimg.com/n2/jfs/t1/64731/3/9170/340030/5dc14d57E1ca5a78e/75ab15c91efd5d4d.jpg", "product_name":"法国兰蔻", "product_price":20},
                ]
            }
        },
        mounted(){
            this.getData();
        },
        methods:{
            getData(){
                let _this = this;
                _this.$http.get('/home').then((res)=>{
                    _this.homeDatas.push(res.data[0]);
                    _this.homeDatas.push(res.data[1]);
                    _this.homeDatas.push(res.data[2]);
                    _this.homeDatas.push(res.data[3]);
                    _this.homeDatas.push(res.data[4]);
                    _this.homeDatas.push(res.data[5]);
                    _this.homeDatas.push(res.data[6]);
                    _this.mainDatas = res.data;
                },(err)=>{
                    console.log(err);
                })
            }
        }
    }
</script>
<style>
    img[lazy=error] {
    background: url('../assets/images/err.png');
  }
</style>