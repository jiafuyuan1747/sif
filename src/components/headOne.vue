<template>
    <view class="icon">
        <img class="imgHead"  :src="src1" alt=""   mode="aspectFill" >
    </view>

</template>

<script>
    export default {
        name: "headOne",
        data(){
            return {
                src1:'/static/5826（1）.png'
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