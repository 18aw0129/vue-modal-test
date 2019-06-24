<template>
  <div id="app">
    <ul class="btn">
      <li v-for="btn in btns" :key="btn.id" class="btn_box">
        <span :class="btn.class" @click="changeCategory($event)" class="btn_box_inner">{{btn.name}}</span>
      </li>
    </ul>

    <div class="modal">
      <div class="modal_box" v-for="item in items" :key="item.id" @click="opanModal(item)" v-show="check = item.all">
        <div class="modal_box_img"><img :src="require('@/assets/img_' + item.id + '.jpg' )" alt=""></div>
        <div class="modal_box_name">{{item.name}}</div>
        <div class="modal_box_discript">{{item.discript}}</div>
      </div>
    </div>
    <transition name="modal">
      <modal :val="postItem" v-if="showModal" @close="closeModal"></modal>
    </transition>
  </div>
</template>

<script>
import modal from '@/components/modal.vue'
export default {
  name: 'app',
  components: {
    modal
  },
  data(){
    return{
      showModal: false,
      postItem: '',
      items:[
        {
          id: "01",
          name: "test01",
          discript: "ここはtest01です",
          all: true,
          odd: true,
        },
        {
          id: "02",
          name: "test02",
          discript: "ここはtest02です",
          all: true,
          even: true,
        },
        {
          id: "03",
          name: "test03",
          discript: "ここはtest03です",
          all: true,
          odd: true,
        },
        {
          id: "04",
          name: "test04",
          discript: "ここはtest04です",
          all: true,
          even: true,
        },
        {
          id: "05",
          name: "test05",
          discript: "ここはtest05です",
          all: true,
          odd: true,
        },
        {
          id: "06",
          name: "test06",
          discript: "ここはtest06です",
          all: true,
          even: true,
        },
        {
          id: "07",
          name: "test07",
          discript: "ここはtest07です",
          all: true,
          odd: true,
        },
      ],
      btns:[
        {name:"全部",class:"btn01"},
        {name:"奇数",class:"btn02"},
        {name:"偶数",class:"btn03"},
      ],
      Category: "btn01"
    }
  },
  mounted(){
    document.querySelector(".btn01").setAttribute('data-state', 'active')
  },
  methods:{
    opanModal(item){
      this.postItem = item;
      this.showModal = true
      document.querySelector('body').style.overflow = "hidden"
    },
    closeModal(){
      this.showModal = false
      document.querySelector('body').style.overflow = "visible"
    },
    changeCategory(event){
      if(this.Category != event.target.className){
        let box = document.querySelectorAll('.btn_box_inner')
        for (var i = 0; i < box.length; ++i) {
          box[i].removeAttribute('data-state')
        }
        this.Category = event.target.className
        event.target.setAttribute('data-state', 'active')
      }
    }
  }
}
</script>

<style lang="scss">
ul, li{
  list-style: none;
}
.btn{
  display: flex;
  max-width: 300px;
  justify-content: center;
  margin: 30px auto;
  li{
    width: 30%;
    span{
      border: 1px solid #000;
      padding: 5px 10px;
      line-height: 1.2;
      transition: all .1s ease-in;
      cursor: pointer;
      &:hover{
        color: #fff;
        background: #000;
      }
      &[data-state="active"]{
        color: #fff;
        background: #000;
      }
    }
  }
}
.modal{
  display: grid;
  gap: 20px 10px;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  max-width: 1300px;
  margin: 0 auto;
  justify-items: center;
  &_box{
    width: 250px;
    height: 300px;
    border-radius: 5px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    &_img{
      width: 100%;
      height: 50%;
      img{
        width: 100%;
        height: 100%;
        object-fit: cover;;
      }
    }
    &_name{
      padding: 10px 10px 0;
    }
    &_discript{
      padding: 10px;
    }
  }
}
.modal-enter{
  opacity: 0;
}
.modal-enter-to{
  opacity: 1;
}
.modal-enter-active{
  transition: opacity 300ms ease-in, transform 300ms ease-in;
}
.modal-leave{
  opacity: 0;
}
.modal-leave-to{
  opacity: 0;
}
.modal-leave-active{
  transition: opacity 270ms ease-out, transform 270ms ease-out;
}
</style>
