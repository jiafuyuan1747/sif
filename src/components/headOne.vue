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
                src2: null,
            }
        },
        methods:{
            getPic(){
                console.log(this + '外面');
                let that = this;
                wx.request({
                    url: 'https://www.lovelivesupport.com/api.php/card/cn/info/1004', //仅为示例，并非真实的接口地址
                    header: {
                        'content-type': 'application/json' // 默认值
                    },
                    success (res) {
                        console.log(res.data);
                        console.log(res.data.response.card_nor_navi.unit_navi_asset);
                        console.log(that + '里面');
                        that.src2 = res.data.response.card_nor_navi.unit_navi_asset;
                        console.log(that.src2);
                    }
                })
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