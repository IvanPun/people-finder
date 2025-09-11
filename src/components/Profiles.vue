<template>
    <div class="card">
        <div class="inside-card">
            <div class="icon">
                <el-image :src="profile.gender == '男' ? boyImg : girlImg" />
            </div>
            <div class="info">
                <p>{{ profile.name }}</p>
                <p>{{ profile.school }}</p>
                <p>{{ profile.major }}</p>

                <div class="tags">
                    <p>愛好：</p>
                    <tag v-for="value in profile.hobbies">{{ value }}</tag>
                </div>
            </div>
            <!-- <el-row :gutter="20">
                <el-col :span="8">
                    <el-image :src="profile.gender == '男' ? boyImg : girlImg" />
                </el-col>
                <el-col :span="16">
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
            </el-row> -->
        </div>


    </div>
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
    height: 20vh;
    margin-top: 2.5vh;

    /* 半透明玻璃卡片 */
    background: rgba(255, 255, 255, 0.72);
    border: 1px solid rgba(255, 255, 255, 0.3);
    padding: 3%;

    border-radius: 15px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
}

.inside-card {
    width: 100%;
    height: 100%;
    background: rgba(194, 181, 155, 0.55);
    border-radius: 10px;
    padding: 2.5% 4%;

    display: flex;
}

.icon {
    height: 100%;
    display: flex;
    align-items: center;
    overflow: hidden;
    border-radius: 15px;
    flex-shrink: 0;
}

.icon .el-image {
    width: auto;
    height: 100%;
    border-radius: 15px;
    object-fit: contain;
}

.info {
    flex: 1;
    margin-left: 4%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.info p {
    font-size: 1rem;
}

.tags {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.5rem;
    align-items: center;
}
</style>