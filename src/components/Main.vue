<template>
<!--Header-->
<div id="header"> 
    <h1 id="head1"> 
        <img id="logoimg" src="https://cdn-icons-png.flaticon.com/512/25/25231.png" width="25px" height="25px" >
        <span id="head2">Github</span> <span id="head1">profiles</span>
        <button @click="showSearch" v-if="showContent" class="button">
            <span >CHANGE USERNAME</span>
        </button>
    </h1> 
</div>

<div id="app">
    <div v-if="showContent">
        <div v-if="yasData">
            <!-- Side profile -->
            <div id="left-menu">
                <br>
                <img id="iconImg" src="https://avatars.githubusercontent.com/u/93151140?s=400&u=c3fabac9f4b0cfa947ac2b4058c298df70d1d5b5&v=4"  >
                <br><br>
                <h2 id="userName">{{ name }}</h2>
                <p id="userDesc">{{ bio }}</p>
            </div>
            <!--Main-->
            <div ID="main-area">
                <br>

                <button @click="showRepository" class="btn_nav">
                    <span >Repos</span>
                </button>
                <button @click="showStarred" class="btn_nav">
                    <span>Starred</span>
                </button>



                <br><hr>
                <div @click="showStarred" v-if="showStar" id="innertube" >
                    <p id="message2">This user has no starred repositories</p>
                </div>
                <div @click="showRepository" v-if="showRepos" id="innertube" > 
                    <div id="customInput">
                        <form>
                        <input type="text" v-on:keydown.enter.prevent= "noSearch" placeholder="Filter by name" id="inputProject">
                        
                        </form>
                        <br>
                    </div>   
                    <ul>
                    <li v-for="item in yasminData" :key=(item)>
                    <a v-bind:href="item.url"  target="_blank" >{{item.title}}</a>
                    <p>{{item.desc}}</p>
                    <img src="https://img.icons8.com/external-flaticons-lineal-flat-icons/19/external-coding-language-computer-programming-flaticons-lineal-flat-icons.png">
                    <span id="list">{{item.lang}}</span>
                    <img src="https://img.icons8.com/external-basicons-line-edtgraphics/19/external-Git-branch-coding-basicons-line-edtgraphics.png">
                    <span id="list">{{item.branches}}</span>
                    <br><br>
                    <hr class="divider">
                    <br>
                    </li>
                    </ul>
                </div>
            </div>
        </div>
        <div v-else class="center">
            <p id="message"> Error: Make sure to insert a valid user name</p>
        </div>
    </div>

    <!--Search-->
    <div v-else class="center">
        <form>
            <input type="text" v-model="tempName" v-on:keydown.enter.prevent= "toggleShowContent" placeholder="Insert a username" id="inputUser">
        </form>
  </div>

</div>

</template>

<!---------------------------------------------------------------------------------------------------------->

<script >
export default {
    data() {
    return {
	    showContent: false,
        showRepos: true,
        showStar: false,

        tempName:"",
        yasData:false,

        name:"Yasmin Oliveira",
        bio:"Gamer girl learning vue",
    
    yasminData:[
        {   title:'DesafioYEB',
            desc:'Repositorio destinado para o desafio YEB',
            lang:'Vue',
            branches:1,
            stars:0,
            url:"https://github.com/Y-Oliveira/DesafioYEB",
            userCod:1},

        {   title:'EndlessNightmare_Page',
            desc:'Projeto RocketSeat - JORNADA DO ZERO A PRIMEIRA VAGA',
            lang:'HTML',
            branches:1,
            stars:0,
            url:"https://github.com/Y-Oliveira/EndlessNightmare_Page",
            userCod:1
        },
        {   title:'SwaggerP ',
            desc:'...',
            lang:'React',
            branches:1,
            stars:0,
            url:"https://github.com/Y-Oliveira/SwaggerP",
            userCod:1
        },
        {   title:'SuperLevelUp ',
            desc:'Little project + spare time = fun coding time!',
            lang:'TypeScript',
            branches:1,
            stars:0,
            url:"https://github.com/Y-Oliveira/SuperLevelUp",
            userCod:1
        },
        {   title:'TestT',
            desc:'123',
            lang:'JavaScript',
            branches:1,
            stars:0,
            url:"https://github.com/Y-Oliveira/TesteT",
            userCod:1
        }

        ]
    }

  },
  methods: {
        toggleShowContent() {
        this.showContent =  true

        if("Yasmin" === this.tempName.trim()) {
        this.yasData= true     
        }
    },
        showSearch(){
            this.showContent = false
            this.tempName = ''
            this.yasData= false 
    },
        showRepository(){
            this.showRepos= true
            this.showStar= false
        },

        showStarred(){
            this.showRepos= false
            this.showStar= true
        },
        
        noSearch(){
            window.alert("Sorry! This function is still in development")
        }

  }
}
</script>

<!---------------------------------------------------------------------------------------------------------->

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  color:#696969;
  margin: 0 10px;
}
a {
  color: #42b983;
}

</style>