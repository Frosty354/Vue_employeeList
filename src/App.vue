<template>

<div>
  <pre>
    <!-- {{JSON.stringify(formValues,null)}} -->
    <button @click="deletehandler">delete</button>
  </pre>
</div>
  <h2 v-for="(item,index) in items" :key="item.name"> {{index}} {{item}} </h2>

    <form> 
      <div>
        
        <input type="text" id="name" placeholder="Name"  v-model.trim="formValues.name" required>
        
        <input type="text" id="Job" placeholder="Job" v-model.trim="formValues.job" required>
        <button @click="submitformhandler">Submit</button>
      </div>
    </form>
</template>


<script>



export default {
  name: 'App',
  components:{
    
    },
  data(){
    return{
      
      formValues:{
        name:"",
        job:"",
      },
      
      items:[
        {name:"Charlie",job:"Janitor"},
        {name:"Mac",job:"Bouncer"},
        {name:"Dee",job:"Aspiring Actress"},
        {name:"Dennis",job:"Bartender"},
      ],
      
    }
  },
  methods:{
    submitformhandler(event)
    {var itemarray = this.items.push({
      name: this.formValues.name,
      job: this.formValues.job,
    });
    event.preventDefault();
    
    this.formValues.name="";
    this.formValues.job="";
    return itemarray;
    },

    deletehandler(rowindex){
      return this.items.splice(rowindex,1);
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
