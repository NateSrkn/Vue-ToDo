<template>
<div>
    <div class="fixed-action-btn" v-on:click="toggleNewForm">
        <button class="btn btn-floating">
            <i class="material-icons">
                add
            </i>
        </button>
    </div>

    <div class="col s3" v-show="isAdding">
       <div class="card horizontal">
           <div class="card-stacked">
            <div class="card-content">
                <div class="input-field col s12">
                    <input v-model="newTitle" type="text" class="validate">
                    <label>Title:</label>
                </div>
                <div class="input-field col s12">
                    <input v-model="newDesc" type="text" class="validate">
                    <label>Description:</label>
                </div>
            </div>
           <div class="card-action">
               <i class="material-icons" v-on:click="sendForm" >
                   add
               </i>
               <i class="material-icons right" v-on:click="toggleNewForm">
                   clear
               </i>
           </div>
           </div>
       </div>
   </div>
</div>

</template>

<script>
export default {
    data() {
        return {
            newTitle: '',
            newDesc: '',
            isAdding: false,
        }
    },
    methods: {
        toggleNewForm() {
            this.isAdding = !this.isAdding
            this.newTitle = '';
            this.newDesc = '';
        },
        sendForm() {
            if (this.newTitle.length > 0 && this.newDesc.length > 0) {
                const title = this.newTitle;
                const description = this.newDesc;
                this.$emit('add-to-do', {
                    title,
                    description,
                    isComplete: false
                });
                this.newTitle = '';
                this.newDesc = '';
                this.isAdding = !this.isAdding
            }
        }
    }
}
</script>
