<template>
  <div class="allBlock">
    <div id="infos">
        <div id="name">
            <h1 style="margin-right:5px">{{users.last_name}} </h1>
            <h1 style="margin-right:5px"> {{users.first_name}} </h1>
            <p>#{{users.id}}</p>
        </div>
        <div id="birth">
            <span style="margin-right:5px">Né le</span>
            <p style="margin-right:5px;font-weight:bold">{{birth(users.birth_date)}}</p>
            <img id='groupIcon' src='../assets/Group.svg' alt='group' style="margin-right:5px">
            <p >{{sex(users.sex)}}</p>
        </div>
        <div id="death" v-if="users.death_date" style="display:flex;align-items:center;font-size:12px">
            <span style="margin-right:5px;">Décès le</span>
            <p v-if="users.death_date" style="font-weight:bold;margin-right:5px;">{{death(users.death_date)}}</p>
            <p>({{deathOld(users.death_date,users.birth_date)}}ans)</p>
        </div>
        
        <div id="ipp">
            <span>IPP:</span>
            <p style="font-weight:bold">{{users.ipp}}</p>
        </div>
    </div>
    <div id="searchNav">
        <div id="bar">
            <img src="../assets/Search.svg" alt="search" @click="disp(search)">
            <input id ="input" type="search" v-model="search"  placeholder="Rechercher" >
        </div>
        <div >
            <a style="border-bottom: 2px solid #233C73;color:#233C73;">Documents</a>
            <a>Biologie</a>
            <a>Mouvements</a>
            <a>Séjours</a>
            <a>Phénotypes</a>
            <a>Cohortes</a>
        </div>
    </div>
  </div>
</template>

<script >
import userData from "../assets/data.json";
// import {ref, computed } from "vue";

// let input = ref("");
export default {
  name: 'PatientBlock',

//   props: {
//     search: String
//   },
  data(){
    // const user = ref(userData)
    // const search = ref("");
    // const searchFunction = computed(() => {

    //     return search;
    //     console.log(user);
    //   return user.search.filter((item) => {
    //       console.log(search);
    //     return item.displayed_text.toLowerCase().includes(search.value);
    //   })
    // })
    return {
      users: userData,search:"",
    //   ,searchFunction
    };
  },
//   computed: {
//     inputValue: {
//       get () {
//         // you can right any getter/state here
//         return this.$store.stateName
//       },
//       set (val) {
//         // you can right any getter/state here
//         this.$store.commit('mutationName', val)
//       }
//     }
// },
  // Creating methods
    methods : {
        // Creating function
        birth: function(value){
            var str = value;
            str = str.substr(0,10);
            var date = str.split("-");
            var ret = `${date[2]}/${date[1]}/${date[0]}`; 
            return ret;
        },
        sex: function(value){
            var str = value;
            var ret;
            {str === "F" ? ret="Femme": ret="Homme"}
            return ret;
        } ,
        death: function(value){
            var str = value;
            str = str.substr(0,10);
            var date = str.split("-");
            var ret = `${date[2]}/${date[1]}/${date[0]}`; 
            return ret;
        },
        deathOld:function(value1, value2){
            var death = new Date(value1);
            var birth = new Date(value2);
            var ret = death.getTime() - birth.getTime();
            return Math.floor(ret / 31536000000);
        }
        // onInput(e) {
        //     this.search = e.target.value;
        // }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.allBlock{
    width: 100%;
    height: 186px;
    left: 0px;
    top: 52px;
    display: flex;
    border-bottom: 1px solid #CACDD5;
}
p{
    color:#696F78;
}
#infos{
    width: 20%;
    height: 50%;
    margin-top: 30px;
    padding-left: 40px;
    display:flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
}
#name{
    height: 40%;
    display: flex;
    align-items: center;
    font-size: 12px;
}
#birth{
    height: 30%;
    width: 70%;
    display: flex;
    align-items: center;
    font-size: 12px;
}
#groupIcon{
    height: 12px;
}
#ipp{
    display: flex;
    align-items: center;
    height: 30%;
    font-size: 12px;
}
#searchNav{
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
}
#bar{
    width: 730px;
    height: 40px;
    border: 2px solid #CACDD5;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding-left: 12px;
    margin-bottom: 40px;
}
#input{
    width: 650px;
    height: 80%;
    outline:none;
    border:none;
    font-size: 1rem;
    line-height: 24px;
}
a{
    font-size: 16px;
    line-height: 23px;
    letter-spacing: -0.3px;
    margin-right: 16px;
    color:#696F78;
}
/* a:hover{
    border-bottom: 2px solid #233C73;
    color:#233C73;
} */
</style>