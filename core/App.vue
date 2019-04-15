<template>
    <div id="app">
        <keep-alive
            :include="[...keepAlivePages]">
            <router-view
                :data-page-id="$route.fullPath">
            </router-view>
        </keep-alive>
    </div>
</template>

<script>
import Vue from 'vue';
import {keepAlivePages} from '@/.lavas/router';

export default {
    name: 'app',
    data() {
        return {
            // https://github.com/lavas-project/lavas/issues/112
            keepAlivePages
        };
    },
    methods: {
        
    }
};
</script>

<style lang="stylus">
// @import "./static/font/font.css"
$page-transition-duration = 0.35s

#app
    font-family 'Avenir', Helvetica, Arial, sans-serif
    -webkit-font-smoothing antialiased
    -moz-osx-font-smoothing grayscale
    text-align center
    color #2c3e50
    height 100%

    .app-view
        position absolute
        top 0
        right 0
        bottom 0
        left 0
        -webkit-overflow-scrolling touch
        background white

        &::-webkit-scrollbar
            width 0
            background transparent

        &.transition-slide
            transition transform $page-transition-duration cubic-bezier(0, 0, 0.2, 1)

            &.slide-left-enter
                transform translate(100%, 0)

            &.slide-left-enter-active
                box-shadow 0 0 16px 2px rgba(0, 0, 0, 0.3)

            &.slide-right-enter
                transform translate(-30%, 0)
                transition-timing-function linear

            &.slide-right-leave-active
                transform translate(100%, 0)
                box-shadow 0 0 16px 2px rgba(0, 0, 0, 0.3)
                z-index 99

            &.slide-left-leave-active
                transform translate(-30%, 0)
                transition-timing-function linear

            &.app-view-scroll-enabled,
            &.slide-left-enter-active,
            &.slide-left-leave-active,
            &.slide-right-enter-active,
            &.slide-right-leave-active
                overflow-y auto

        &.transition-fade
            opacity 1
            transition opacity 1s ease

            &.fade-enter
                opacity 0

            &.fade-leave-active
                opacity 0
</style>
