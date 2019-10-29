<template>
    <div class="newMessage">
        <form @submit.prevent="addMessage">
            <label for="newMessage">New Message (Enter to add)</label>
            <input type="text" name="newMessage" v-model="newMessage" autocomplete="off"/>
        </form>
        <p class="red-text">{{ feedback }}</p>
    </div>
</template>

<script>
import db from "@/firebase/init"
export default {
    name: "NewMessage",
    props: ["name"],
    data (){
        return{
            newMessage: null,
            feedback: null
        }
    },
    methods: {
        addMessage(){
            if(this.newMessage){
                this.feedback = null
                db.collection("messages").add({
                    content: this.newMessage,
                    name: this.name,
                    timestamp: Date.now()
                }).catch(err => {
                    console.log(err)
                })
                this.newMessage = null
            }
            else{
                this.feedback = "You must enter a message in order to send one"
            }
        }
    }
}
</script>

<style>

</style>