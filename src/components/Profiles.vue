<template>
    <div class="card">
        <div class="inside-card">
            <div class="card-content">
                <img :src="profile.gender === '男' ? boyImg : girlImg" class="icon" />
                <div class="info">
                    <p class="name"><b>{{ profile.name }}</b></p>
                    <p>{{ profile.school }}</p>
                    <p>{{ profile.major }}</p>
                    
                    <div class="tags">
                        <tag v-for="value in profile.hobbies">{{ value }}</tag>
                    </div>
                </div>
            </div>
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
    margin-top: 2.5vh;

    /* 半透明玻璃卡片 */
    background: rgba(255, 255, 255, 0.72);
    border: 1px solid rgba(255, 255, 255, 0.3);
    padding: 10px;

    border-radius: 15px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
}

.inside-card {
    width: 100%;
    background: rgba(194, 181, 155, 0.55);
    border-radius: 10px;
    padding: 10px 20px;

    display: flex;
    overflow: hidden;
}

.card-content {
    display: flex;
    align-items: center;
    height: 15vh;
}

.icon {
    height: 100%;
    object-fit: contain;
    border-radius: 15px;
}

.info {
    margin-left: 20px;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: start;
    gap: 3px;

}

.info .name{
    font-size: 1.6rem;
}

.info p {
    font-size: clamp(1rem, 1.5vh, 2rem);
}

.tags {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    align-items: center;
}
</style>