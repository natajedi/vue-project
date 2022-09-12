<template> 
  <h1>{{ ToDoApp }}</h1> 
 </template>

<h2>Add a new task</h2>
  <div>   
    <input type="text"     
    v-model="newTask"
    @keyup.enter="addTask"
    placeholder="Add a new task"
    > 
    <button     
    @click="addTask"      
    :disabled="newTask.length < 1" 
    >      
    Add task    
    </button>
  </div>

<span>
You have {{ allTasks }} 
{{ allTasks > 1 ? 'tasks' : 'task' }} 
at the moment
</span>

<div v-if="newTask.length > 0">   
<h3>New task preview</h3>   
 <p>{{ newTask }}</p> 
</div>

<script> 
export default {  
  data() {    
    return {     
       title: 'ToDoApp',
      newTask: [        
        { id: 1, name: 'Learn Vue JS', finished: false },        
        { id: 2, name: 'Build a Vue application', finished: false },        
        { id: 3, name: 'Write an article about Vue JS', finished: false }     
      ]     
    }  
  } 
}  

methods: {  
  computed: {
   addTask() { 
    return this.tasks.length
   },
   latest() {
     return [...this.tasks].reverse()
   }
  }
     if (this.newTask.length < 1) return

    this.tasks.push({       
      id: this.tasks.length + 1,        
      name: this.newTask,        
      finished: false      
    });

      this.newTask = ''    
    }  
  }
<ul>    
  <li v-for="(task, index) in latest" :key="task.id">        
    {{ index + 1 }}. {{ task.name }}

    <div v-if="task.finished">            
      <button @click="removeTask(task.id)">Delete task</button>        
      </div>    
  </li> 
</ul>
</script>

<style>
@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
</style>
