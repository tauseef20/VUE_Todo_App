<template>
  <div>
    <h1>Welcome to Todo App Task Manager</h1>
    <div class="main">
      <div class="input">
        
    <input type="text" placeholder="Enter your Todo Task" v-model="add" required> 
    {{error}}
    <button v-on:click= "addtodo" v-show="trueValue" >Submit</button>
    <button v-on:click= "update"  v-show="falseValue" >Update</button>
    </div>
    
    <div class="showtodo" v-if="RenderComponent">
      <div class="Show" v-for="(Item ,Index) in showtext" :key="Index">
        <div class="show-Item">{{Item.text}}
          <i v-on:click="remove(Index)" class="fa fa-trash"></i>
          <i v-on:click="edit (Item)" class="fa fa-edit"></i>
        </div>
        <!-- {{showtext}} -->
        </div>
     
    </div>
    <div class="footer">
      <button v-on:click="clear">Clear All</button>
    </div>
    </div>
    
    
  </div>
</template>

<script>
export default {
name:'TodoCard',
data (){
  return{
    add:"",
    showtext:[],
    error:"",
    UpdateId:null,
    RenderComponent:true,
    trueValue: true,
      
  }
},
methods:{
  addtodo (){
    if(this.add){
      const id= this.showtext.length+1
    const data = {
      id,
      text:this.add
    }
    this.showtext.push(data),
    this.add="";
    }
    else{
      this.error=("Task is Required")
    }
    
    // console.log("Hello")
    // alert("Hello")
    
  },
  remove(delet){
    this.showtext.splice(delet,1)
  },
  clear(){
    this.showtext=[];
  },
  edit(Item){
    this.add = Item.text
    this.UpdateId=Item.id
    this.falseValue=true,
    this.trueValue=false
  },
update(){
  this.RenderComponent=false
  const obj= this.showtext.find((Item)=>Item.id==this.UpdateId)
  const index=this.showtext.indexOf(obj)
  this.showtext[index]={
    id:this.UpdateId,
    text:this.add
  }
  this.UpdateId=null,
  this.RenderComponent=true
  this.add="";
  this.falseValue=false,
    this.trueValue=true
}
 
}

}
</script>

<style>
body{
    width: 100%;
    height: 100vh;
    /* overflow: hidden; */
    padding: 10px;
    background: linear-gradient(to bottom, #68EACC 0%, #497BE8 100%);
  }
  h1{
    text-align: center;
  }
  .main{
    background: #fff;
    max-width: 600px;
    width: 100%;
    margin: 120px auto;
    padding: 25px;
    border-radius: 5px;
    box-shadow: 0px 10px 15px rgba(0,0,0,0.1);
  }
  .main .input{
    margin: 20px 0;
    width: 100%;
    display: flex;
    height: 45px;
  }
  .input input{
    width: 85%;
    height: 100%;
    outline: none;
    border-radius: 3px;
    border: 1px solid #ccc;
    font-size: 17px;
    padding-left: 15px;
    transition: all 0.3s ease;
  }
  .input input:focus{
    border-color: #8E49E8;
  }
  .input button{
    width: 80px;
    height: 100%;
    border: none;
    color: #fff;
    margin-left: 5px;
    font-size: 21px;
    outline: none;
    background: #8E49E8;
    cursor: pointer;
    border-radius: 3px;
    
  }
  .main .showtodo{
    max-height: 250px;
    overflow-y: auto;
  }
  .showtodo .show-Item {
    position: relative;
    /* display: flex;
    flex-direction: row ; */
    list-style: none;
    height: 45px;
    line-height: 45px;
    margin-bottom: 8px;
    background: #f2f2f2;
    border-radius: 3px;
    padding: 0 15px;
    cursor: default;
    overflow: hidden;
  }
  .showtodo .show-Item i{
    float: right;
    margin: 10px;
    cursor: pointer;
  }
  /* .showtodo .show-Item i{
    position: absolute;
    right: -45px;
    color: #fff;
    width: 45px;
    height: 80px;
    text-align: center;
    border-radius: 0px 3px 3px 0px;
    background: #e74c3c;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  .showtodo .show-Item:hover i{
    right: 0px;
  }
  
  .showtodo .show-Item .icon{
    position: absolute;
    right: -45px;
    background: #e74c3c;
    width: 45px;
    height: 45px;
    align-self: center;
    color: #fff;
    border-radius: 0 3px 3px 0;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  .showtodo .show-Item:hover i{
    right: 0px;
  } */
  .main .footer{
    display: flex;
    width: 100%;
    margin-top: 20px;
    align-items: center;
    justify-content: space-between;
  }
  .footer button{
    /* float: right; */
    padding: 6px 10px;
    border-radius: 3px;
    border: none;
    outline: none;
    color: #fff;
    font-weight: 400;
    font-size: 16px;
    margin-left: 5px;
    /* margin-top: 30px; */
    background: #8E49E8;
    cursor: pointer;
    user-select: none;
  }

</style>