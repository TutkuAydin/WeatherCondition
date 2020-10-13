<template>
  
<div id="app" >
   <main>

   <div class="search-box">
        <input 
          type="text" 
          class="search-bar" 
          placeholder="Search..."
          v-model="query"
          @keypress="fetchWeather"
        />
    </div>
    <div v-if="looding==false" >
      <nav>
        <v-toolbar class="background2" height="50em">
           
            <v-toolbar-title >
                <span class="title" style="font-size : 1em" >Detailed 7-day weather for {{this.city}}</span>
                
            </v-toolbar-title>
           
        </v-toolbar>
       </nav>
  <div class="headlinefirst">Current Wether({{ dateBuilder(0) }})</div>
  <v-container fluid>
      <v-row dense>
       <v-col>

        <v-card
        class="cardfirst"
        width="1100"
        height="98"
         >

        
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
                   </v-img>
                    <v-list-item-title class="deg"> {{translate(data.daily[0].temp.day)}} °c  

                        <div class="node">  Felt Temperature {{translate(data.daily[0].feels_like.day)}} °c</div>
                     </v-list-item-title>
                   <v-list-item>
                      <v-img   src="../assets/rein.png" height="80px" width="80px"></v-img>
                      <v-list-item-title class="info">{{data.daily[0].weather[0].main}} </v-list-item-title>
                       </v-list-item>
                  <v-list-item>
                       <v-img   src="../assets/windy.png" height="80px" width="80px"> </v-img>
                       <v-list-item-title class="info">{{data.daily[0].wind_speed}} metre/sec</v-list-item-title>
                  </v-list-item>
                     <v-list-item>
                       <v-img   src="../assets/pressure.png" height="80px" width="80px"> </v-img>
                       <v-list-item-title class="info">{{data.daily[0].pressure}}  hPa</v-list-item-title>
                  </v-list-item>
             </v-list-item>
          
              </v-card>
           </v-col>

      </v-row>
  </v-container>
  <v-container fluid>
      <v-row dense>
       <v-col>

        <v-card
        class="card"
        width="400"
        height="350"
         >
         <div class="headline">{{ dateBuilder(1) }}</div>
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
                   </v-img>
                  <v-list-item-title class="deg"> {{translate(data.daily[1].temp.day)}} °c  

                    <div class="node">  Felt Temperature {{translate(data.daily[1].feels_like.day)}} °c</div>
                  </v-list-item-title>
                 
             </v-list-item>
             <v-list-item>
                <v-img   src="../assets/rein.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[1].weather[0].main}} </v-list-item-title>
            </v-list-item>
             <v-list-item>
                   <v-img   src="../assets/windy.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[1].wind_speed}} metre/sec</v-list-item-title>
             </v-list-item>
               <v-list-item>
                   <v-img   src="../assets/pressure.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[1].pressure}} hPa</v-list-item-title>
             </v-list-item>

           


  </v-card>
  </v-col>
 <v-col>

        <v-card
        class="card"
        width="400"
        height="350"
         >
         <div class="headline">{{ dateBuilder(2) }}</div>
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                   
                  <v-list-item-title class="deg">{{translate(data.daily[2].temp.day)}} °c
                     <div class="node">  Felt Temperature {{translate(data.daily[2].feels_like.day)}} °c</div>
                  </v-list-item-title>
             </v-list-item>
             <v-list-item>
                <v-img   src="../assets/rein.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[2].weather[0].main}} </v-list-item-title>
            </v-list-item>
             <v-list-item>
                   <v-img   src="../assets/windy.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[2].wind_speed}} metre/sec</v-list-item-title>
             </v-list-item>
            <v-list-item>
                   <v-img   src="../assets/pressure.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[2].pressure}} hPa</v-list-item-title>
             </v-list-item>
           


  </v-card>
  </v-col>
<v-col>

        <v-card
        class="card"
        width="400"
        height="350"
         >
         <div class="headline">{{ dateBuilder(3) }}</div>
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="deg">{{translate(data.daily[3].temp.day)}} °c

                     <div class="node">  Felt Temperature {{translate(data.daily[3].feels_like.day)}} °c</div>
                  </v-list-item-title>
             </v-list-item>
             <v-list-item>
                <v-img   src="../assets/rein.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[3].weather[0].main}} </v-list-item-title>
            </v-list-item>
             <v-list-item>
                   <v-img   src="../assets/windy.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[3].wind_speed}} metre/sec</v-list-item-title>
             </v-list-item>

            <v-list-item>
                   <v-img   src="../assets/pressure.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[3].pressure}} hPa</v-list-item-title>
             </v-list-item>
           


     </v-card>
   </v-col>
        
  </v-row>
  </v-container>
  <v-container fluid>
  <v-row dense>
       <v-col>

        <v-card
        class="card"
        width="400"
        height="350"
         >
         <div class="headline">{{ dateBuilder(4) }}</div>
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="deg">{{translate(data.daily[4].temp.day)}} °c

                     <div class="node">  Felt Temperature {{translate(data.daily[4].feels_like.day)}} °c</div>
                  </v-list-item-title>
             </v-list-item>
             <v-list-item>
                <v-img   src="../assets/rein.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[4].weather[0].main}} </v-list-item-title>
            </v-list-item>
             <v-list-item>
                   <v-img   src="../assets/windy.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[4].wind_speed}} metre/sec</v-list-item-title>
             </v-list-item>

               <v-list-item>
                   <v-img   src="../assets/pressure.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[4].pressure}} hPa</v-list-item-title>
             </v-list-item>
           


      </v-card>
  </v-col>
 <v-col>

        <v-card
        class="card"
        width="400"
        height="350"
         >
         <div class="headline">{{ dateBuilder(5) }}</div>
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="deg">{{translate(data.daily[4].temp.day)}} °c
                     <div class="node">  Felt Temperature {{translate(data.daily[5].feels_like.day)}} °c</div>
                  </v-list-item-title>
             </v-list-item>
             <v-list-item>
                <v-img   src="../assets/rein.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[5].weather[0].main}} </v-list-item-title>
            </v-list-item>
             <v-list-item>
                   <v-img   src="../assets/windy.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[5].wind_speed}} metre/sec</v-list-item-title>
             </v-list-item>

              <v-list-item>
                   <v-img   src="../assets/pressure.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[5].pressure}} hPa</v-list-item-title>
             </v-list-item>
           


  </v-card>
  </v-col>
  <v-col>

        <v-card
        class="card"
        width="400"
        height="350"
         >
         <div class="headline">{{ dateBuilder(6) }}</div>
             <v-list-item>
                   <v-img   src="../assets/tempture.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="deg">{{translate(data.daily[6].temp.day)}} °c
                     <div class="node">  Felt Temperature {{translate(data.daily[6].feels_like.day)}} °c</div>
                  </v-list-item-title>
             </v-list-item>
             <v-list-item>
                <v-img   src="../assets/rein.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[6].weather[0].main}} </v-list-item-title>
            </v-list-item>
             <v-list-item>
                   <v-img   src="../assets/windy.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[6].wind_speed}} metre/sec</v-list-item-title>
             </v-list-item>

              <v-list-item>
                   <v-img   src="../assets/pressure.png" height="80px" width="80px"> 
                     
            
                   </v-img>
                  <v-list-item-title class="info">{{data.daily[6].pressure}} hPa</v-list-item-title>
             </v-list-item>
           


          </v-card>
        </v-col>
      </v-row>
    </v-container>



     </div>

    
    <div v-if="looding==true">       
      <p>Lodding</p>  
      
    </div>
   </main>
  </div>

  
</template>



<script>
export default {
  name: 'app',

  data () {
    return {
      api_key: '140dc31ce66d8d47beac6b6b2c2a0d37',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      data:{},
      looding:null,
      lon:{},
      lat:{},
      city:{},
      degree:{},
    }
        
  },
  methods:{

    
   //for take data from current weather
    fetchWeather (e) {
      if (e.key == "Enter") {
     this.looding=true
        fetch(`${this.url_base}weather?q=${this.query}&appid=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
  //take location from the data
    setResults (results) {
      this.lon= results.coord.lon;
      this.lat= results.coord.lat;
      this.city=results.name
      this.fetchWeathersecond();
     
    
    },
   fetchWeathersecond () {
     //https://api.openweathermap.org/data/2.5/onecall?lat={lat}&lon={lon}&exclude={part}&appid={YOUR API KEY}

      //take 7 day weather data with use this location
        this.looding=true
        fetch(`${this.url_base}onecall?lat=${this.lat}&lon=${this.lon}&exclude=current,minutely,hourly&appid=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResultssecond);
      },
    
  setResultssecond (results) {
      this.data = results;
      this.looding=false
    
    },
    //translate kelvin to celsius
    translate(kelvin){
      return Math.round(kelvin-273.15);
    
    },

      //for take date (becaouse there arent data info in data)
      dateBuilder (k) {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
      let newday;
     let date;
       let month;
       let day;
      if(k==0){ // current day
         day= days[d.getDay()];
         date = d.getDate();
         month = months[d.getMonth()];
      }
      if(k==1){ 
             //if-else control for the days array need repetition or not
            if(d.getDay()+1<=5){
              day= days[d.getDay()+1];
            }
            else{
             newday=(d.getDay()+1) % 7
             day=days[newday]

           }
         date = d.getDate()+1;
         
        }
      if(k==2){
            if(d.getDay()+2<=4){
              day= days[d.getDay()+2];
           }
           else{
             newday=(d.getDay()+2) % 7
             day=days[newday]

           }
          date = d.getDate()+2;
         
        }
      if(k==3){
           if(d.getDay()+3<=3){
              day= days[d.getDay()+3];
           }
           else{
             newday=(d.getDay()+3) % 7
             day=days[newday]

           }
           
          date = d.getDate()+3;
         
        }
      if(k==4){
           if(d.getDay()+4<=2){
              day= days[d.getDay()+4];
           }
           else{
             newday=(d.getDay()+4) % 7
             day=days[newday]

           }
          date = d.getDate()+4;
        
        }
      if(k==5){
           if(d.getDay()+5<=1){
              day= days[d.getDay()+5];
           }
           else{
             newday=(d.getDay()+5) % 7
             day=days[newday]

           }
          date = d.getDate()+5;
        
        }
      if(k==6){
          if(d.getDay()+6<=6){
              day= days[d.getDay()+6];
           }
           else{
             newday=(d.getDay()+6) % 7
             day=days[newday]

           }          
           date = d.getDate()+6;
        
        }
      
      //for change month , when the instant date is the last day of the month 
      if((d.getDate()==31 && (months[d.getMonth()]=="July"||"August"||"October"||"December"||"January"||"March"||"May"))
         ||(d.getDate()==30 && (months[d.getMonth()]=="September"||"November"||"April"||"June")) 
         ||(d.getDate()==28 && (months[d.getMonth()]=="February"))){
          month = months[d.getMonth()+1];
         }
      else{
         month = months[d.getMonth()];
    
      return `${day} ${date} ${month}`;
    }
   
  }

          
}
}

</script>






<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

#app {
  /*background-image: url('./assets/cold-bg.jpg');*/
  background-color:white;
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}



main {
  min-height: 100vh;
  padding: 25px;
  background:white;
  /*background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));*/
}

.search-box {
  width: 20%;
  margin-bottom: 30px;
  margin-left: 550px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  
  color: #313131;
  font-size: 20px;

  appearance: none;
  border:none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}


.location-box .location {
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #FFF;
  font-size: 20px;
  font-weight: 300;
  margin-left: 200px;
  }
.headline{
    font-size: 20px;
  
     margin-left: 130px;
    
   font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;

}
.headlinefirst{
    font-size: 20px;
  
     margin-top: 50px;
    
   font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    margin-left: 200px;
}
.deg{
  font-size:30px ;
  color: red;
   margin-left: 10px;
   
}

.card{
  margin-top: 50px;
  margin-left: 40px;
  
}
.cardfirst{
   margin-left:150px;
}
.info{
    margin-left: 10px;
    font-size:70px ;
}
.background2{
  background-image: url('../assets/darksky.jpg');
}
.title{
   font-size:70px ;
   color: #FFF;
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;

  }
.node{
  font-size:12px ;
   color:black;
}

</style>
