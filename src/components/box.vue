<template>
<div id='app'>
    <label class="three">select tabs:</label>
    <input type="text">
    <multiselect 
    class="one"
    
    placeholder="choose mulitselect"
    select-label='' selected-label='' deselect-label='' v-model='value'
    :options='options'
    :multiple='true' track-by='name' :custom-label="nameWithLang"
    :close-on-select='false'  
    @select=onSelect($event) @remove=onRemove($event)
    >
    <span class='checkbox-label' slot='option' slot-scope='scope' @click.self='select(scope.option)'>
        {{scope.option.name}}
        <input class='test' type='checkbox' v-model='scope.option.checked' @focus.prevent/>
        </span>
        </multiselect>
        <pre class=" two">{{value}}</pre>
        </div>
        </template>
            
    <script>
    import Multiselect from 'vue-multiselect'
    
    export default {
    components:{
        Multiselect
    },
    data(){
        return{
            value:[],
            options:[
            {name: 'fsd' },
             {name: 'fascd' },
              {name: 'JavaScript'},
            ]
        }
    },
    methods:{
         nameWithLang ({  name,library }) {
      return `${library} — [${name}]`
    },
       
        onSelect(option) {
            option.checked=true;
        },
        onRemove(option) {
            option.checked=false;
        }
    }
    }
 </script>
 <style scoped>
     *{
         background-color: blueviolet;
     }
 .one{
     width: 20%;
     margin-left: 40%;
 }
 * {
  font-family: 'Lato', 'Avenir', sans-serif;
}

.checkbox-label {
  display: block;
}
.two{
   margin-left: 40%;
}

.test {
  position: absolute;
  right: 40vw;
}
.three{
    margin-left: 45%;
    margin-top: 10%;
}
 </style>