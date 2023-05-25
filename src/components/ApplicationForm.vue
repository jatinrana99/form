<template>
<h1>APPLICATION FORM</h1>

<!-- form code -->
<form v-on:submit.prevent>
First Name <input type="text" placeholder="Enter First Name" v-model="fname">
Last Name <input type="text" placeholder="Enter Last Name"  v-model="lname">
Address <input type="text" placeholder="Enter Address" v-model="address">
<button v-on:click="getFormData" type="button">Add</button>
<button>Update</button>
<button>Delete</button>
<!-- update and delete button is not working , I have to work on it -->
</form>


<!-- for displaying the data -->
<table>
    <tc v-for="(item,index) in info" v-bind:key="index">
       <td>
        {{ item }}
       </td> 
    </tc>
</table>
</template>


<script>



    export default{
        name:`ApplicationForm`,
        // props:{
        //     fname
        // },
        data(){
            return{   
            fname:"",
            lname :"",
            address:"",
            info:[

            ]
            }
        },
        methods: {
            getFormData(){
                console.warn(this.fname , this.lname , this.address);
                this.info.push(this.fname);
                this.fname = "";
                this.info.push(this.lname);
                this.lname = "";
                this.info.push(this.address);
                this.address = "";
            },
            // cond(){
            //     if(tc<=3){
                    
            //     }
            }
        }
    
    
 
</script>


<style scoped>

</style>