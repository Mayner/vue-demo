<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img width="64" height="64" :src="seller.avatar" alt="">
            </div>
            <div class="content">
                <div class="title">
                    <div class="brand"></div>
                    <div class="name">{{seller.name}}</div>
                </div>
                <div class="description">
                    {{seller.description}}/{{seller.deliveryTime}}分钟送达
                </div>
                <div v-if="seller.supports" class="support">
                    <span class="icon" :class="classMap[seller.supports[0].type]"></span>
                    <span class="text">{{seller.supports[0].description}}</span>
                </div>
            </div>
            <div v-if="seller.supports" class="support-count" @click="showDetail">
                <span class="count">{{seller.supports.length}}个</span>
                <i class="icon-keyboard_arrow_right"></i>
            </div>
        </div>
        <div class="bulletin-wrapper"  @click="showDetail">
            <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
            <i class="icon-keyboard_arrow_right"></i>
        </div>
        <div class="background">
            <img :src="seller.avatar" alt="" width="100%" height="100%">
        </div>
        <div v-show="detailShow" class="detail">
            <div class="detail-wrapper clearfix">
                <div class="detail-main">
                    <h1 class="name">{{seller.name}}</h1>
                </div>
            </div>
            <div class="detail-close" @click="hideDetail">
                <i class="icon-close"></i>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
    export default {
        props: {
            seller: {
                type: Object
            }
        },
        data() {
            return {
                detailShow: false
            };
        },
        methods: {
            showDetail() {
                this.detailShow = true;
            },
            hideDetail() {
                this.detailShow = false;
            }
        },
        created() {
            this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
        }
    };
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixin"
    .header
        position: relative
        color: rgb(255, 255, 255)
        background: rgba(7, 17, 27, 0.5)
        overflow: hidden
        .content-wrapper
            position: relative
            padding: 24px 12px 18px 24px
            font-size: 0
            .avatar
                display: inline-block
                margin-right: 16px
                vertical-align: top
                img
                    border-radius: 2px
            .content
                display: inline-block
                .title
                    font-weight: bold
                    line-height: 18px
                    .brand
                        display: inline-block
                        vertical-align: top
                        width: 30px
                        height: 18px
                        bg-image('brand')
                        background-size: 30px 18px
                        background-repeat: no-repeat
                    .name
                        display: inline-block
                        margin-left: 6px
                        font-size: 16px
                .description
                    margin: 8px 0 10px
                    font-size: 12px
                    line-height: 12px
                .support
                    .icon
                        display: inline-block
                        width: 12px
                        height: 12px
                        vertical-align: top
                        &.decrease
                            bg-image('decrease_1')
                        &.discount
                            bg-image('discount_1')
                        &.guarantee
                            bg-image('guarantee_1')
                        &.invoice
                            bg-image('invoice_1')
                        &.special
                            bg-image('special_1')
                        background-size: 12px 12px
                        background-repeat: no-repeat
                    .text
                        margin-left: 4px
                        font-size: 10px
                        line-height: 12px
            .support-count
                position: absolute
                height: 24px
                line-height: 24px
                padding: 0 8px
                border-radius: 14px
                background-color: rgba(0,0,0,0.2)
                right: 12px
                bottom: 14px
                .count
                    font-size: 10px
                    line-height: 24px
                    text-align: center
                .icon-keyboard_arrow_right
                    font-size: 10px
                    margin-left: 2px
        .bulletin-wrapper
            position: relative
            padding: 0 22px 0 12px
            height: 28px
            line-height: 28px
            white-space: nowrap
            overflow: hidden
            text-overflow: ellipsis
            background: rgba(7, 17, 27, 0.2)
            .bulletin-title
                display: inline-block
                vertical-align: top
                margin-top: 8px
                width: 22px
                height: 12px
                font-size: 10px
                bg-image('bulletin')
                background-size: 22px 12px
                background-repeat: no-repeat 
            .bulletin-text
                vertical-align: top
                margin: 0 4px
                font-size: 10px
            .icon-keyboard_arrow_right
                position: absolute
                font-size: 10px
                right: 12px
                top: 9px
        .background
            position: absolute
            top: 0
            left: 0
            width: 100%
            height: 100%
            z-index: -1
            filter: blur(10px)
        .detail
            position: fixed
            z-index 100
            left: 0
            top: 0
            width: 100%
            height 100%
            overflow: auto
            background: rgba(7, 17, 27, 0.8)
            .detail-wrapper
                min-height: 100%
                width 100%
                .detail-main
                    margin-top: 64px
                    padding-bottom: 64px
                    .name
                        font-size 16px
                        font-weight 700
                        line-height 16px
                        text-align center
            .detail-close
                position: relative
                height: 32px
                width: 32px
                margin: -64px auto 0 auto
                clear: both
                font-size: 32px
                color: rgba(255, 255, 255, 0.5)
</style>
