<template>
    <view>
        <text>test component 2</text>
<!--        <img src="https://images.weserv.nl/?url=https://www.lovelivesupport.com/asset/assets/image/units/u_normal_navi_33105001.png" alt="">-->
        <ul v-if="picUrl.length">
            <li v-for="item in picUrl" :key="item">
                <img :src="item" alt="">
            </li>
<!--            <li v-for="item in picUrl" :key="item">{{ item }}</li>-->
        </ul>

    </view>
</template>

<script>
    export default {
        name: "cardsInfo",
        props:{
            cardID: Number,
        },
        data(){
            return{
                picUrl:[],
                id: 2333,
            }
        },
        created () {
            let that = this;
            console.log(that.cardID);
            console.log(`https://www.lovelivesupport.com/api.php/card/cn/info/${that.cardID}`);
            wx.request({
            url: `https://www.lovelivesupport.com/api.php/card/cn/info/${that.cardID}`, //仅为示例，并非真实的接口地址
            header: {
                'content-type': 'application/json' // 默认值
            },
            success (res) {
                console.log(res.data);
                // console.log(res.data.response.card_nor_navi.unit_navi_asset);
                const url =  'https://images.weserv.nl/?url='
                    + 'https://www.lovelivesupport.com/asset/'
                    + res.data.response.card_nor_navi.unit_navi_asset;
                that.picUrl.push(url);
                console.log(that.picUrl)
            }
        });
        },

    }
</script>

<style scoped>

</style>