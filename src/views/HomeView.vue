<script>

export default {


  data() {
    return {
      goal:[],
      goalValue:'',
      
      drivers:"study vue",
      error:" error" ,
     counter: 10,
     name:'',
     mName:'',
     FullName:'',
     boxa:'false',
     boxb:'false',
     boxc:'false',
     obj:{
      name:'mona',
      age:23,
     }


     
      // Add other validation rules for the title field
    };

  },

  methods: {

    selecte(box){
      if(box=='a'){
        this.boxa= !this.boxa;
;
      }
      else if(box=='b'){
        this.boxb= !this.boxb;
;


      }
      else if(box=='c'){
        this.boxc= !this.boxc;


      }

        


      

    },
    outputGoal(){
      const randomNum= Math.random();
      if (randomNum > .5){
        return this.drivers;
      }
      else{
        return this.error;
      }
    },
    add(num){
      this.counter=this.counter+num;
    },
    reduce(num){
      this.counter=this.counter-num;
    },
    setName(event , lastName){
      this.name=event.target.value+" "+lastName;

    },
    submit(){
      alert('hello mona')
    },
    confirmName(){
      this.mName=this.name;

    },
    reset(){
      this.name='';
    },
    printFullName(){
     if(this.name ==''){
      return '';
      
     }
     else{
      return this.name+" "+'MAHMOUD';
     }
    },
    addGoal(){
    console.log(this.goalValue)
    this.goal.push(this.goalValue);



  },
  removeGoal(index){
    console.log(index)
    this.goal.splice(index,1)
  },


   
  },
 
  

  watch:{
    name(value){
      this.FullName=value==''? '':value+'Mahmoud'


    },
    counter(value){
      if(value>40){
        this.counter =0;
      }
    }

  },
  computed: {
    // fullName(){
    //   // console.log("heeeeey..");
    //   // return this.name==''? '':this.name+'MAHMOUD';

    // }
 
  },
};
</script>

<template>
  <main>
    <header>
      <h1>Monster Slayer</h1>
    </header>
    





    <TheWelcome />
    <h2>events in action</h2>
    <div> {{outputGoal()}} </div>


    <button v-on:click.right="add(20)"> Add</button>
    <br>
    <button v-on:click.left="reduce(5)">reduce</button>
    <p v-once>starting value: {{counter}}</p>
    <p>Result: {{ counter }} </p><br>


    <input type="text" v-model="name"/>
     <button  v-on:click="reset()">resetName</button>



    <form action="" v-on:submit.prevent="submit()">
      <input type="text"  />
      <button v-on:click="reset()">submit</button>





    </form>
    <p>{{FullName}}</p><br>
    

   <input  type="text"  name="demo" class="dem"
   :class="{active: boxa}" @click="selecte('a')"/>

   <input  type="text" name="demo" class="dem" 
   :class="{active: boxb}" @click="selecte('b')"/> 

    <input  type="text"  name="demo" class="dem"
   :class="{active: boxc}" @click="selecte('c')"/>


   <input type="text" v-model="goalValue"/>
   <button @click="addGoal">Add Goal</button> 
   <p>{{goal}}</p>
   <button  @click="removeGoal(index)">remove</button>
   <div v-for="(gol,index) in goal" :key="gol">
       <p @click="removeGoal(index)">{{gol}}</p>
   </div>

   <p v-if="goal.length == 0">no goal have been add yet</p>
   <ul v-else>
     <li v-for="hello , index in goal" :key="hello" @click="removeGoal(index)" > 
      <p>{{hello}}:{{index}}</p>
      <input type="text" @click.stop>
 

     </li>
    
   </ul>

  
</template>
