<template>
<h1>APPLICATION FORM</h1>

<!-- form code -->
<section>
    <form v-on:submit.prevent>
        <div>
            First Name <input type="text" placeholder="Enter First Name" v-model="fname">
        </div>
        <div>
            Last Name <input type="text" placeholder="Enter Last Name"  v-model="lname">
        </div>
        <div>
            
            Address <input type="text" placeholder="Enter Address" v-model="address">
        </div>
<button v-on:click="getFormData()" type="button">ADD</button>
<!-- <button>Update</button> -->
<!-- update and delete button is not working , I have to work on it -->
</form>    
</section>



<!-- for displaying the data -->
<b-table>
    <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Address</th>
    <th>Color</th>
    <th>Delete</th>
    </tr>
 
    <tr v-for="(item,index) in info " v-bind:key="index">
        
        <td :style="tdStyle"> {{ item.fname }} </td>
        <td :class="{red: isRed}"> {{ item.lname }} </td>
        <td :class="{red: isRed}"> {{ item.address }} </td>
        


        <td>
            <input v-on:click="isRed=!isRed" type="checkbox"/>
        </td>
    <td>
            <button v-on:click.prevent="deleteFormData(index) "> X </button>
        </td>

    </tr>
</b-table>
</template>


<script>



    export default{
        name:`ApplicationForm`,
        bgColor: {
      type: String,
      default: "#41b883"
    },
        data(){
            return{   
            fname:"",
            lname :"",
            address:"",
            info:[ ],
            isRed:false,
            activeColor:'red'
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

            },
            computed:{
                tdStyle(){
                    return{
                        "background-color":this.bgColor
                    }
                }
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
    border: solid 2px;
}
td{
    border: solid 2px;
    background-color: rgb(188, 188, 102);
}
.red {
  color: red;
}

section div{
    margin: 12px;
    padding: 4px;
}
</style>