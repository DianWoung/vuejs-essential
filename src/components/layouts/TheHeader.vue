<template>
    <div class="navbar navbar-default topnav">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" @click="toggleNav">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>

                <a href="/" class="navbar-brand">
                    <span class="title">{{ logo.title }}</span>
                    <img :src="logo.src" :alt="logo.title">
                </a>
            </div>

            <div id="top-navbar-collapse" :class="['collapse', 'navbar-collapse', { in: showCollapsedNav }]">
                <ul class="nav navbar-nav">
                    <li v-for="(item, index) in navList" :class="{ active: index === activeNavIndex }" :key="item">
                        <a href="#" @click="changeNavIndex(index)">{{ item }}</a>
                    </li>
                </ul>
                 <!-- 入口组件 -->
            <div class="navbar-right">
                <TheEntry />
            </div>
            </div>
           
        </div>
    </div>
</template>
  
<script>
import TheEntry from '@/components/layouts/TheEntry'
export default {
    name: 'TheHeader',
    components: {
        TheEntry
    },
    data() {
        return {
            logo: {
                src: `${this.uploadsUrl}sites/ByvFbNlQYVwhvTyBgLdqitchoacDNznN.jpg`,
                title: 'Learnku Vue.js'
            },
            navList: ['社区', '头条', '问答', '教程'],
            activeNavIndex: 0,
            showCollapsedNav: false
        }
    },
    beforeCreate() {
        this.uploadsUrl = 'https://learnku.com/vuejs/uploads/'
    },
    methods: {
        changeNavIndex(index) {
            this.activeNavIndex = index
        },
        toggleNav() {
            this.showCollapsedNav = !this.showCollapsedNav
        }
    }
}
</script>
  
<style scoped>
.title {
    display: none;
}

.navbar-default .navbar-nav>.active>a {
    background: rgba(0, 0, 0, .03);
}</style>