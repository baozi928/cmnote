<template>
  <div id="note" class="detail">
    <note-sidebar></note-sidebar>
    <div id="note-detail"></div>
    <h1>notebookId : {{ $route.query.notebookId }}</h1>
    <h1>noteId : {{ $route.query.noteId }}</h1>
  </div>
</template>

<script>
  import Auth from '@/apis/auth'
  import NoteSidebar from "./NoteSidebar.vue";

  export default {
    components:{
      NoteSidebar
    },
    data () {
      return {
        msg: '笔记详情列表'
      }
    },
    created() {
      Auth.getInfo()
        .then(res => {
          if(!res.isLogin) {
            this.$router.push({ path: '/login' })
          }
        })
    },
    methods:{

    }
  }
</script>

<style scoped>
  @import url(../assets/css/note-detail.less);

  #note {
    display: flex;
    align-items: stretch;
    background-color: #fff;
    flex: 1;
  }
</style>
