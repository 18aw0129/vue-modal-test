<template>
    <div id="modal">
        <div class="modal_bg" @click="$emit('close')"></div>
        <div class="m_box">
            <div class="m_box_img"><img :src="require('@/assets/img_' + val.id + '.jpg' )" alt=""></div>
            <div class="m_box_text">
                <div class="m_box_text_name">{{val.name}}</div>
                <div class="m_box_text_discript">{{val.discript}}</div>
            </div>
        </div>
        
    </div>
</template>

<script>
export default {
    name:"modal",
    props:{
        val: Object
    }
}
</script>

<style lang="scss">
#modal{
    position: fixed;
    top: 0; left: 0;
    .modal_bg{
        position: fixed;
        height: 100%; width: 100%;
        top: 0; left: 0;
        opacity: 0.3;
        background: #000;
        z-index: 1;
    }
    .m_box{
        position: fixed;
        z-index: 2;
        width: 720px; height: 480px;
        background: #fff;
        top: calc(50% - 240px); left: calc(50% - 360px);
        border-radius: 5px;
        display: flex;
        &_img{
            width: 50%;
            height: 100%;
            img{
                width: 100%;
                height: 100%;
                object-fit: cover;;
            }
        }
    }
}
</style>
