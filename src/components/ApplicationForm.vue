<template>
<h1>APPLICATION FORM</h1>

<!-- form code -->
<form v-on:submit.prevent>
First Name <input type="text" placeholder="Enter First Name" v-model="fname">
Last Name <input type="text" placeholder="Enter Last Name"  v-model="lname">
Address <input type="text" placeholder="Enter Address" v-model="address">
<button v-on:click="getFormData()" type="button">ADD</button>
<!-- <button>Update</button> -->
<!-- update and delete button is not working , I have to work on it -->
</form>


<!-- for displaying the data -->
<table>
    <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Address</th>
    <th>Color</th>
    <th>Delete</th>
    </tr>
 
    <tr v-for="(item,index) in info " v-bind:key="index">
        
        <td :class="{red: isRed}"> {{ item.fname }} </td>
        <td :class="{red: isRed}"> {{ item.lname }} </td>
        <td :class="{red: isRed}"> {{ item.address }} </td>

        
        <td>
            <input v-on:click="isRed=!isRed" type="checkbox"/>
        </td>
    <td>
            <button v-on:click.prevent="deleteFormData(index) "> Delete </button>
        </td>

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
            isRed:false,
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
            deleteFormData(index){
                
                    this.info.splice(index,1);

                
            },


            }
        }
    
    
 
</script>


<style scoped>
table{
    border : solid brown;
    position: absolute;
    width: 1045px;
    left: 170px;
    
}
th{
    border: solid green;
}
td{
    border: solid yellow;
}
.red {
  color: red;
}
</style>