<template>
    <view class="icon">
        <img class="imgHead"  :src="src1" alt=""   mode="aspectFill" >
        <input type="text" @click="getPic" value="'try me">
    </view>

</template>

<script>
    export default {
        name: "headOne",
        data(){
            return {
                src1:'/static/5826.png',
                src2: 'https://www.lovelivesupport.com/asset/',
            }
        },
        methods:{
            getPic(){
                let that = this;
                console.log(this + '外面');
                wx.request({
                    url: 'https://www.lovelivesupport.com/api.php/card/cn/info/1004', //仅为示例，并非真实的接口地址
                    header: {
                        'content-type': 'application/json' // 默认值
                    },
                    success (res) {
                        console.log(res.data);
                        console.log(res.data.response.card_nor_navi.unit_navi_asset);
                        const urlSec = res.data.response.card_nor_navi.unit_navi_asset;
                        that.src1 = 'https://images.weserv.nl/?url=' + that.src2 + urlSec;
                    }
                });
                console.log('test getPic');
            }
        }
    }
</script>

<style lang="scss">
    .icon{
        width: 187.5rpx;
        height: 187.5rpx;
        overflow: hidden;
        display: flex;
        .imgHead{
            width: 187.5rpx;
            height: 187.5rpx;
        }
    }


</style>