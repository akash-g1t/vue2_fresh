<template>
     <div>

         <form @submit="addTodo">
             <input type='text' v-model='title' name='title' placeholder='Add Todo...'>
             <input type="submit" value="Submit" class="btn">
         </form>

     </div>
</template>

<script>

export default {
    name: 'AddTodo',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            console.log('Went to addTodo!')
            const newTodo = {
                title: this.title,
                completed: false
            }
            // Send up to parent
            console.log(newTodo)
            this.$emit('add-todo', newTodo);

            this.title = ''
        }
    }
}
</script>

<style scoped>

    form {
        display: flex;
    }

    input[type='text'] {
        flex: 10;
        padding: 5px;
    }

    input[type='submit'] {
        flex: 2;
    }

</style>


// For preventing the form submit default behaviour,

// Either use "@submit.prevent" in <form> tag i.e.
// <form @submit.prevent="addTodo">

// OR

// use an "event" listener in the methods and add event.preventDefault(), i.e.

// methods: {
//     addTodo(e) {
//         e.preventDefault();
//         const newTodo = {
//             ...
//         }
//     }
// }