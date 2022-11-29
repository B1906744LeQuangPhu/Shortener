<template>
    <h1>404</h1>
    <div class="fs-5" v-if="!this.$store.state.isAuthenticated">
        Quay lại
        <router-link :to="{ name: 'Home' }" style="text-decoration: none"> 
            Trang Chủ
        </router-link>
        
    </div>
</template>