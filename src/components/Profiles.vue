<template>
    <el-card class="card">
        <el-row :gutter="20">
            <el-col :span="12">
                <el-image :src="profile.gender == '男' ? boyImg : girlImg" />
            </el-col>
            <el-col :span="12">
                <div class="info">
                    <p>{{ profile.name }}</p>
                    <p style="font-size: 1rem; margin-top: 0.5rem;">{{ profile.school }}</p>
                    <p style="font-size: 1rem;">{{ profile.major }}</p>
                    <p style="font-size: 1rem;">愛好：</p>
                    <div class="tags">
                        <tag v-for="value in profile.hobbies">{{ value }}</tag>
                    </div>
                </div>


            </el-col>
        </el-row>

    </el-card>
</template>

<script setup>
import tag from './tag.vue';

const props = defineProps({
    profile: Object
})

const boyImg = "/images/boy.jpg"
const girlImg = "/images/girl.jpg"
</script>

<style scoped>
.card {
    width: 90vw;
    margin-top: 5vh;

    /* 半透明玻璃卡片 */
    background: rgba(255, 255, 255, 0.25);
    border: 1px solid rgba(255, 255, 255, 0.3);
    backdrop-filter: blur(12px);
    /* 背景模糊 */
    -webkit-backdrop-filter: blur(12px);

    border-radius: 20px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
}

.el-image {
    width: 100%;
    border-radius: 15px;
    object-fit: contain;
}

.info {
    height: 100%;
    display: flex;
    flex-direction: column;

}

.tags {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.5rem;
}
</style>