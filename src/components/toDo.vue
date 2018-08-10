<template>
<div class="col s12 m3">
    <div class="card horizontal small" v-if="!isEditing">
        <div class="card-stacked">
            <div class="card-content">
                <h5>{{todo.title}}</h5>
                <p>{{todo.description}}</p>
            </div>
            <div class="card-action">
                <label>
                    <input type="checkbox" class="filled-in" v-model="todo.isComplete">
                    <span></span>
                </label>
                <div class="right">
                    <i class="material-icons" v-on:click="toggleEditForm">edit</i>
                    <i class="material-icons" v-on:click="deleteToDo(todo)">delete</i>
                </div>
            </div>
        </div>
    </div>

       <div class="card horizontal small" v-else-if="isEditing" >
           <div class="card-stacked">
            <div class="card-content">
                <div class="input-field col s12">
                    <input v-model="todo.title" type="text" class="valid">
                    <label class="active" >Title:</label>
                </div>
                <div class="input-field col s12">
                    <input v-model="todo.description" type="text" class="valid">
                    <label class="active" >Description:</label>
                </div>
            </div>
           <div class="card-action">
               <i class="material-icons" v-on:click="toggleEditForm" >
                   save
               </i>
           </div>
           </div>
       </div>
</div>
</template>

<script>
export default {
    props: ['todo'],
    data() {
        return {
            isEditing: false
        }
    },
    methods: {
        toggleEditForm() {
            this.isEditing = !this.isEditing
        },
        deleteToDo(todo) {
            this.$emit('delete-to-do', todo)
        }
    }
}
</script>
