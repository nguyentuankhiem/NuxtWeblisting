<template>
    <div>
        <vue-glide>
            <vue-glide-slide v-for="i in 5" :key="i">
                {{ i }}
                <img src="https://vnn-imgs-f.vgcloud.vn/2021/04/12/18/can-ho-studio.jpg">
            </vue-glide-slide>
        </vue-glide>
    </div>
</template>



<script>
    import 'vue-glide-js/dist/vue-glide.css'
    import { Glide, GlideSlide } from 'vue-glide-js'

    export default 
    {
        components: 
        {
            [Glide.name]: Glide,
            [GlideSlide.name]: GlideSlide
        }
    }
</script>