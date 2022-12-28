<template>
    <div>
        <ball-c :ball="inner" @play-ball="getChild"></ball-c>
    </div>
</template>
<script>
import BallC from './BallC.vue'
export default {
    name: 'BallP',
    components: {
        BallC
    },
    data: function() {
        return {
            inner: 0
        }
    },
    methods: {
        getChild(ball) {
            console.log('子级提给我的是', ball)
            this.inner = ball + 1;
        }
    }
}
</script>
