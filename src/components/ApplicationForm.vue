<template>
<h1>APPLICATION FORM</h1>

<!-- form code -->
<form v-on:submit.prevent>
First Name <input type="text" placeholder="Enter First Name" v-model="fname">
Last Name <input type="text" placeholder="Enter Last Name"  v-model="lname">
Address <input type="text" placeholder="Enter Address" v-model="address">
<button v-on:click="getFormData()" type="button">Add</button>
<!-- <button>Update</button>
<button v-on:click="deleteFormData()" type="button">Delete</button> -->
<!-- update and delete button is not working , I have to work on it -->
</form>


<!-- for displaying the data -->
<table>
    <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Address</th>
    <th>Color</th>
    </tr>
 
    <tr v-for="(item,index) in info " v-bind:key="index">
        
        <td> {{ item.fname }} </td>
        <td>{{ item.lname }}</td>
        <td>{{ item.address }}</td>
    </tr>
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
            info:[ ],
            }
        },
        methods: {
            getFormData(){
                console.warn(this.fname , this.lname , this.address);
                this.info.push({'fname':this.fname,'lname': this.lname,'address':this.address});
                this.fname = "";

                this.lname = "";
                
                this.address = "";
            },
            // deleteFormData(){

            // },
                // num(index){
                //     return index
                // }

            }
        }
    
    
 
</script>


<style scoped>
table{
    border : solid;
}
</style>