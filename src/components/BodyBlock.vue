<template>
    <div class="documents">
        <div class="amount">
            <img src="../assets/Clipboard.svg" alt="clipboard">
            <p >{{users.documents.length}} documents</p>
        </div>
        <div class="list">
            <Categorie/>
            <div v-for="(user,index) in getTab(users.documents)" :key="index" style="display:flex;">
                <div v-if="idDoc!==index" style="display:flex;width: 1350px;border-bottom: 1px solid #D6D7DF;">
                    <div id='date1'>
                        <p >{{user.document_date.substr(0,4)}}</p>  
                    </div>
                    <div id='date2'>
                        <p >{{user.document_date.substr(8)}}</p>
                        <p >{{getMonth(user.document_date.substr(5,2))}}</p>  
                    </div>
                    <div id='type'>
                        <img src="../assets/Newspaper.svg" alt="type">
                        <p >{{user.document_type}}</p> 
                    </div>
                    <div id='origin'>
                        <p >{{user.document_origin_code}}</p>  
                    </div>
                    <div id='apercu' >
                        <div id='title' >
                            <p> {{user.title}}</p>
                        </div>
                        <div id="text">
                            <span v-html="cleanStr(user.displayed_text)"></span>
                        </div>
                    </div>
                    <div id='more'>
                        <img src='../assets/CaretRight.svg' alt='more' style="width:24px" @click="showFull(index)" >  
                    </div>
                </div>
                <div v-else style="display:flex;flex-direction:column;border-bottom: 1px solid #D6D7DF;">
                    <div style="background-color:#F4F5F9;display:flex;width: 1350px;height:54px">
                        <div id='date1'>
                            <p >{{user.document_date.substr(0,4)}}</p>  
                        </div>
                        <div id='date2'>
                            <p >{{user.document_date.substr(8)}}</p>
                            <p >{{getMonth(user.document_date.substr(5,2))}}</p>  
                        </div>
                        <div id='type'>
                            <img src="../assets/Newspaper.svg" alt="type">
                            <p >{{user.document_type}}</p> 
                        </div>
                        <div id='origin'>
                            <p >{{user.document_origin_code}}</p>  
                        </div>
                        <div id='apercu' >
                        </div>
                        <div id='more'>
                            <img src='../assets/CaretDown.svg' alt='more' style="width:24px" @click="showFull(index)" >  
                        </div>
                    </div>
                    <div style="display:flex;flex-direction:column;margin:20px 20px">
                        <div id='titleFull' >
                            <p> {{user.title}}</p>
                        </div>
                        <span v-html="cleanStr(user.displayed_text)"></span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
import userData from "../assets/data.json";
import Categorie from './Categorie.vue';

export default {
    components: { Categorie },
    name: 'BodyBlock',
    props:{
        search:String
    },
    data() {
        return {
         users: userData,isMore: true,idDoc : null
        };
    },
    computed:{
        // disp(str){
        //     console.log(str);
        //     return str
        // },
    },
    methods:{
        
        getTab(value){
            let tab = [];
            tab = [...value];
            tab.sort((t1,t2) => t1.document_date > t2.document_date ? -1 : 1);
            return tab
        },
        getMonth(value){
            let ret = '';
            value === '01' ? ret = "janv":
            value === '02' ? ret = "fev":
            value === '03' ? ret = "mars":
            value === '04' ? ret = "avr":
            value === '05' ? ret = "mai":
            value === '06' ? ret = "juin":
            value === '07' ? ret = "juil":
            value === '08' ? ret = "aout":
            value === '09' ? ret = "sept":
            value === '10' ? ret = "oct":
            value === '11' ? ret = "nov":
            ret = "dec";
            return ret;
        },
        showFull(index){
            if (this.idDoc === index) {
                this.idDoc = null;
                return;
            }
            this.idDoc = index;
        },
        cleanStr(str){
            return str.replace(/(\\n)*(\\t)*/g, "");
        }
        // getIconType(value){
            // let ret = "../assets/Newspaper.svg";
            // value === "Journal Article" ? ret = "../assets/Newspaper.svg":
            // value === "Comparative Study" ? ret = "../assets/Clipboards.svg" :
            // ret = "../assets/Book.svg";
        //     console.log("value",value);
        //     return value;
        // }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* .isMore {
  background-color: green;
} */
.documents{
    padding: 10px 40px;
    background-color: #F8F9F9;
}
.amount{
    display: flex;
}
.list{
    border-radius: 10px;
    background-color: white;
    width: 1350px;
    border: 2px solid #D6D7DF;
}
#date1{
    width: 70px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding-left: 10px;
}
#date2{
    width: 60px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}
#type{
    width: 180px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}
#origin{
    width: 180px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}
#apercu{
    width: 790px;
    height: 104px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    text-overflow: ellipsis;
}
#more{
    width:54px;
    display: flex;
    justify-content: center;
}
#title{
    height: 30%;
    display: flex;
    align-items: center;
    margin-left: 20px;
    font-weight: bold;
}
#titleFull{
    height: 30%;
    display: flex;
    align-items: center;
    width: 1100px;
    font-weight: bold;
}
#text{
    height: 3rem;
    margin-left: 20px;
    line-height: 1.5rem;
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
}

</style>