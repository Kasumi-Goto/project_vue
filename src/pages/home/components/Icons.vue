<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page, index) of pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" />
                    </div>
                    <p class="icon-desc">{{ item.desc }}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
export default {
    name: 'HomeIcons',
    props: {
        list: Array
    },
    data: function () {
        return {
            swiperOption: {
                autoplay: false
            }
        }
    },
    computed: {
        pages: function () {
            const pages = []
            this.list.forEach((item, index) => {
                // 让第9个小图标展示在第2页上
                const page = Math.floor(index / 8)
                if (!pages[page]) {
                    pages[page] = []
                }
                pages[page].push(item)
            })
            return pages
        }
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
.icons >>> .swiper-container
//让swiper小图标轮播的高度是两栏而不是一张图标高度，宽高比是2
    height: 0
    padding-bottom: 50%
.icons
    margin-top: .1rem
    .icon
        //小图标每个宽高都是25%
        position: relative
        overflow: hidden
        float: left
        width:25%
        height: 0
        padding-bottom: 25%
        .icon-img
            position: absolute
            top: 0
            left: 0
            right: 0
            bottom: .44rem
            // 给图标间距
            box-sizing: border-box
            padding: .1rem
            .icon-img-content
                //图标居中显示
                display: block
                margin: 0 auto
                height: 100%
        .icon-desc
            position: absolute
            left: 0
            right: 0
            bottom: 0
            height: .44rem
            line-height: .44rem
            color: $darkTextColor
            text-align: center
            ellipsis()
</style>
