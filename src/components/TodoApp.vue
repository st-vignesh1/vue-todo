<template lang="pug">
  div(class="w-full flex justify-center items-center h-screen bg-indigo-950")
    div(class="w-[30%] min-h-[50vh] bg-white rounded-xl p-4")
      h1(class="p-2 text-indigo-900 font-semibold text-xl mb-2 pl-6") {{ msg }}
      div(class="w-full flex justify-center items-center pl-6 pr-6 relative mb-4")
        input(class="border border-gray-200 rounded-3xl w-full h-11 bg-gray-200 p-4 outline-none text-sm" placeholder="Add your task" v-model.trim="task")
        button(class="absolute right-6 bg-orange-600 w-24 h-11 rounded-3xl text-white font-medium" @click="addTask") ADD
  
      ul(v-if="allTask.length>0" class="w-full pl-6 pr-6")
          li(v-for="(task) in allTask" :key="allTask.id" class="pl-4 capitalize font-medium text-gray-500")
            | {{task.title}}
            button(class="rounded-full w-10 h-10" @click="removeTask(task.id)") x

</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: "TodoApp",
  data(){
     return {
      task:"",
      allTask:[]
    }
  },
  methods:{
    addTask(){
      if(this.task!=="")
      this.allTask.push({id:uuidv4(),title:this.task,status:"todo"})
      console.log(this.allTask)
      this.task=""
    },
    removeTask(id){
      this.allTask=this.allTask.filter(task=>task.id!==id)
    }
  },
  props: {
    msg: {
      type: String,
    },
  },
};
</script>
