<template>
  <h3>ToDo List</h3>
  <ListAdd :writeEdit="writeEdit" :Edit="Edit" :memo="memo" :save="save" @memowrite ="memo = $event"/>

  <List :Edit="Edit" :todolist="todolist" @statusControl="statusControl" @statusdelete="statusdelete" @statusEdit="statusEdit"/>

  
</template>

<script>

import ListAdd from './components/ListAdd.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  data() {
    return {
      memo : null,
      todolist : [],
      done : null,
      Edit : false,
      Eidtnumber : null,

    }
  },
  components: {
    ListAdd,
    List
  },
  methods : {
    save() {
      if(this.memo === null) {
        alert('할일 작성')
      } else {
        this.todolist.unshift({memo : this.memo, status : 'created'})
        this.memo = null
      }
    },
    statusControl(i,status) {
      this.todolist[i].status = status
    },
    statusdelete(i) {
      this.todolist.splice(i,1)
    },
    statusEdit(i) {
      this.memo = this.todolist[i].memo
      this.Edit = true
      this.Eidtnumber = i
    },
    writeEdit() {
      this.todolist[this.Eidtnumber].memo =  this.memo
      this.Edit = false
      this.memo = null
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin: 0px;
}
div {
  box-sizing: border-box;
}
.write {
  width: 45%;
  position: relative;
  left: 800px;
}
.listcontainer {
  width: 45%;
  position: relative;
  left: 150px;
  bottom: 175px;
}
.list {
  background: rgba(248, 248, 242, 0.922);
  width: 500px;
  height: 150px;
  margin: 10px;
  box-shadow: 5px 5px 5px gray;
}
.list p {
  padding-top: 40px;
}
.btns img {
  width: 30px;
  height: 30px;
  margin: 30px 10px;
  cursor: pointer;
}
.writebtn {
  margin-left: 290px;
  margin-top: 10px;
  background: blue;
  color: white;
  border: 1px solid blue;
  width: 90px;
  height: 30px;
  border-radius: 5px;
  cursor: pointer;
}


</style>
