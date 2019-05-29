<!-- List.vue 函数式组件 -->
<template functional>
    <div>
        <p v-for="(item,index) in props.items" @click="props.itemClick(item)" :key="index">
            {{ item }}
        </p>
    </div>
</template>
