<template>
    <div>
        <div class="recommend-title">热销推荐</div>
        <ul>
            <!-- 1像素边框 -->
            <router-link
                tag="li"
                :to="'/detail/' + item.id"
                class="item border-bottom"
                v-for="item of list"
                :key="item.id"
            >
                <img :src="item.imgUrl" class="item-img" />
                <div class="item-info">
                    <p class="item-title">{{ item.title }}</p>
                    <p class="item-desc">{{ item.desc }}</p>
                    <button class="item-button">查看详情</button>
                </div>
            </router-link>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'HomeRecommend',
    props: {
        list: Array
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.recommend-title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
.item
    overflow: hidden
    display: flex
    height: 1.9rem
    .item-img
        height: 1.7rem
        width: 1.7rem
        padding:.1rem
    .item-info
    // 自动撑开宽度
        flex: 1
        padding:.1rem
        overflow hidden
        .item-title
            line-height: .54rem
            font-size: .32rem
            ellipsis()
        .item-desc
            line-height: .4rem
            color: #ccc
            ellipsis()
        .item-button
            line-height: .44rem
            margin-top: .16rem
            background: #ff9300
            padding: 0 .2rem
            border-radius: .06rem
            color: #fff
</style>
