<template>
  <div class="listcontainer">
    <div v-for="(list,i) in todolist" :key="i" class="list" :class="{'done' : list.status === 'done', 'created' : list.status === 'created'}">
     <p>{{list.memo}}</p>
     <div class="btns">
     <img v-if="list.status === 'created'" @click="$emit('statusControl',i,'done')" src="../assets/check.png" alt="">
     <img v-else @click="$emit('statusControl',i,'created')" src="../assets/refresh.png" alt="">
     <img @click="$emit('statusdelete',i)" src="../assets/garbisy.png" alt="">
     <img v-if="list.status === 'created'" @click="$emit('statusEdit',i), Edit == true"  src="../assets/Edit.png" alt="">
     </div>
    </div>
  </div>
  {{done}}
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props : {
        todolist : Array,
        done : String,
        Edit : Boolean,
    }
}
</script>

<style>
.done p {
  text-decoration: line-through;
  color: silver;
}
.done {
  background: rgba(0, 0, 0, 0.1);
}
</style>