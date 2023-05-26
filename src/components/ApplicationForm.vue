<template>
    <h1>APPLICATION FORM</h1>
    <BaseButton :alert="reverseMessage"  name="Reverse the Name"  />
    <p>Your Current String : {{ message }}</p>
    <input type="text" v-model="message">
    <BaseButton  :alert="getMessage" name="Alert"></BaseButton>
   
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
<table>
    <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Address</th>
    <th>Color</th>
    <th>Delete</th>
    </tr>
 
    <tr v-for="(item,index) in info " v-bind:key="index">
        
        <td :class="{red: isRed}" > {{ item.fname }} {{ index }} </td>
        <td :class="{red: isRed}"> {{ item.lname }} {{ index }}</td>
        <td :class="{red: isRed}"> {{ item.address }} {{ index }}</td>
        


        <td>
            <!-- <input v-on:click="isRed=!isRed" type="checkbox"/> -->
            <input v-on:click="isRed=!isRed" key="index" type="checkbox"/>{{ index }}
        </td>
    <td>
        <!-- <i class="fa fa-trash-o"  v-on:click.prevent="deleteFormData(index) "></i> -->
        <i class="fa-solid fa-trash" v-on:click.prevent="deleteFormData(index) "></i>
            <!-- <button v-on:click.prevent="deleteFormData(index) "> <i class="fa fa-trash-o" aria-hidden="true"></i> -->
  <!-- </button> -->
            <!-- <img alt="Vue logo" src="./assets/logo.png" v-on:click.prevent="deleteFormData(index)" > -->
        </td>

    </tr>
</table>

<br>
<br>
<!-- <button v-on:click="reverseMessage">Reverse Message</button> -->

</template>


<script>
import BaseButton from './BaseButton.vue'



    export default{
        name:`ApplicationForm`,
        components:{
            BaseButton
        },
        data(){
            return{   
                fname:"",
                lname :"",
                address:"",
                info:[ ],
                isRed:false,
                activeColor:'red',
                clickColor:true,
                // message: "I Am Developer",
                message:""
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

            getMessage(){
                alert("Hello from parent");
            },
            reverseMessage: function() {
              this.message = this.message.split('').reverse().join('');
              
        }

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

.my::v-deep .my1 {
  background-color: aqua;
  margin: 5px;
  border:2px solid;
  border-radius: 29%;
  height: 78px;
  width: 135px;
}
</style>