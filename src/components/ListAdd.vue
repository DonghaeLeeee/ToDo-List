<template>
    <div class="write">
  <textarea :value = "memo" @input="$emit('memowrite',$event.target.value)" cols="50" rows="10"></textarea> <br>
  
  <button v-if="Edit == false" class="writebtn" @click="save"> 리스트 작성</button>
  <button v-if="Edit == true" class="writebtn" @click="writeEdit"> 리스트 수정</button>

  </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props : 
        ['memo','save','Edit','writeEdit'],
}
</script>

<style>

</style>