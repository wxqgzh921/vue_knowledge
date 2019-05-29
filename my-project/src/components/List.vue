<!-- List.vue 函数式组件 -->
<template functional>
    <div>
        <p v-for="item in props.items" @click="props.itemClick(item)">
            {{ item }}
        </p>
    </div>
</template>
