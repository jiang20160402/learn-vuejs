<template>
    <div class="navtitle">
        <div class="line"></div>
        <div class="text">{{ title }}</div>
        <div class="line"></div>
    </div>
</template>

<script>
  export default {
    props: ['title']
  }

</script>


<style lang="stylus">
    @import("../../common/stylus/mixin")

    .navtitle
        display: flex
        width: 80%
        margin: 30px auto 24px auto
        .line
            flex: 1
            position: relative
            top: -6px
            border-bottom: 1px solid rgba(255, 255, 255, 0.2)
        .text
            padding: 0 12px
            font-weight: 700
            text-size: 14px
</style>
