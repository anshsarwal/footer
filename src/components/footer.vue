<template>
  <v-app>
    <div>
    <v-container fluid class="pa-0">
      <v-layout row wrap class="lay">
        <!-- Policy Info -->
        <v-flex lg3 md3 sm3 xs3 id="policyInfo" >
          <v-list>
            <!-- <v-list-tile> -->
                <v-list-tile-title>
                  {{ title1 }}
                </v-list-tile-title>
            <!-- </v-list-tile> -->
            <!-- <v-list-tile > -->
              <!-- <v-list-tile-content> -->
                <v-list-tile-sub-title v-for="(info, i) in footerInfos1" :key="i">
                  {{ info.children }}
                </v-list-tile-sub-title>
              <!-- </v-list-tile-content> -->
            <!-- </v-list-tile> -->
          </v-list>
        </v-flex>
        <!-- Company -->
        <v-flex lg3 md3 sm3 xs3 id="company">
          <v-list>
            <!-- <v-list-tile> -->
              <!-- <v-list-tile-content> -->
                <v-list-tile-title>
                  {{ title2 }}
                </v-list-tile-title>
              <!-- </v-list-tile-content> -->
            <!-- </v-list-tile> -->
            <!-- <v-list-tile > -->
              <!-- <v-list-tile-content> -->
                <v-list-tile-sub-title v-for="(info, i) in footerInfos2" :key="i">
                  {{ info.children }}
                </v-list-tile-sub-title>
              <!-- </v-list-tile-content> -->
            <!-- </v-list-tile> -->
          </v-list>
        </v-flex>
        <!-- Need Help -->
        <v-flex lg3 md3 sm3 xs3 id="needHelp">
          <v-list>
            <!-- <v-list-tile> -->
              <!-- <v-list-tile-content> -->
                <v-list-tile-title>
                  {{ title3 }}
                </v-list-tile-title>
              <!-- </v-list-tile-content> -->
            <!-- </v-list-tile> -->
            <!-- <v-list-tile > -->
              <!-- <v-list-tile-content> -->
                <v-list-tile-sub-title v-for="(info, i) in footerInfos3" :key="i">
                  {{ info.children }}
                </v-list-tile-sub-title>
              <!-- </v-list-tile-content> -->
            <!-- </v-list-tile> -->
          </v-list>
        </v-flex>
        <!-- Subscribe -->
        <v-flex lg3 md3 sm3 xs3 id="Subscribe">
          <v-list>
            <!-- <v-list-tile> -->
              <!-- <v-list-tile-content> -->
                <v-list-tile-title>
                  {{ title4 }}
                </v-list-tile-title>
              <!-- </v-list-tile-content> -->
            <!-- </v-list-tile> -->
          </v-list>
          <!-- For Email -->
          <v-flex xs10 offset-xs1 id="email" class="form-group">
            <v-form>
              <input type="email" name="Email" placeholder="E-Mail" v-model="email" >
            <span v-if="email.length > 1">{{ email_msg }}</span>
            <v-flex class="text-xs-center buttonflex">
              <v-btn depressed small id="button" :class="{active: disable_btn}" :disabled="disable_btn" @click.prevent="subscribe" type="submit">SUBSCRIBE</v-btn>
            </v-flex>
            </v-form>
            
          </v-flex>  
        </v-flex>
      </v-layout>
    </v-container>
    <!-- Please Connect With Us -->
    <v-container fluid class="pa-0">
      <v-layout row wrap class="lay">
        <v-flex xs12 class="text-xs-center connect" style="padding-top: 5px;">
          Please Connect With Us
        </v-flex>
        <!-- All The Social Media Icons -->
        <v-flex lg4 offset-lg4 md4 offset-md4 sm4 offset-sm4 xs4 offset-xs4 class="lol">
          <v-btn v-for="icon in icons" :key="icon" icon class="ml-5">
            <v-icon size="16px">{{ icon }}</v-icon>
          </v-btn>
        </v-flex>
      </v-layout>
    </v-container>
    <!-- Copyright -->
    <v-container fluid class="pa-0">
      <v-layout row wrap class="lay">
        <v-flex class="text-xs-center ending" style="padding-top: 3px; padding-bottom: 3px">
          &copy;2018 — <strong>SkyLim InfoTech Pvt Ltd</strong>
        </v-flex>
      </v-layout>
    </v-container>
    </div>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      email: '',
      email_msg: '',
      disable_btn: true,
      title1: 'POLICY INFO',
      title2: 'COMPANY',
      title3: 'NEED HELP',
      title4: 'SUBSCRIBE',
      footerInfos1:[
        {children:'Privacy Policy'}, {children:'Terms Of Sales'}, {children:'Terms Of Use'}, {children:'Report Abuse and TakeDown Policy'}
      ],
      footerInfos2:[
        {children:'About Us'}, {children:'Core Values'}, {children:'Blogs'}, {children:'Careers'}, {children:'SiteMap'}
      ],
      footerInfos3:[
        {children:'FAQ'}, {children:'Contact Us'},        
      ],
      icons: ['fab fa-facebook', 'fab fa-twitter', 'fas fa-at', 'fab fa-linkedin'],
    }),

    watch: {
      email: function(value) {
        this.valid_email(value, 'email_msg');
      }
    },

    methods: {
      valid_email(email, msg) {
        if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email)) {
          this[msg] = '';
          this.disable_btn = false;
          return true;
        } else {
          this[msg] = 'Keep typing untill the email is valid';
          this.disable_btn = true;
          return false;
        } 
      },

      subscribe () {
        axios.post(`http://jsonplaceholder.typicode.com/posts`, {
          email: this.email
          })
          .then(response => {
          console.log(response)
          })
          .catch(e => {
          })
          disable_btn = true
          email_msg = ''
          email = ''
      }
    }
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.lay{
  font-family: 'Open Sans', arial, Verdana, Tahoma, sans-serif;
  border: solid lightgray 1px;
}
/*List Styling*/
.list__tile__title{
  font-size: 16px;
  text-align: center;
  padding-bottom: 40px;
  /* border: solid black 1px; */
}
.list__tile__sub-title{
  font-size: 12px;
  text-align: center;
  color: black!important;
  /* border: solid black 1px; */
} 
/* .connect{
  border: solid black 1px;
} */
/* .lol{
  border: solid black 1px;  
} */
/* #subscribe{
  border: solid black 1px;
} */
#email{
  /* border:solid black 1px; */
  margin-top: -20px;
}
.connect{
  font-size: 16px;
}
/*For The Hovering Button*/
#button{
  border: solid 2px deepskyblue;
  color: deepskyblue;
  background-color: white;
}
#button:hover{
  color: white;
  background-color: deepskyblue;
}
/*For Everything in the input field*/
input{
    width: 100%;
    border-bottom: solid lightgray 1px;
    outline: none;
    padding: 10px 1px;
    margin: 5px;
} 
input:hover{
    border-bottom: solid black 1px;
}
input:focus{
    border-bottom: deepskyblue solid 2px;
} 
input::-webkit-input-placeholder {
 font-family: 'Open Sans', arial, Verdana, Tahoma, sans-serif;
 -webkit-transition: all 0.5s ease-in-out;
 transition: all 0.5s ease-in-out;
}
input:focus::-webkit-input-placeholder, input:valid::-webkit-input-placeholder {
 color: deepskyblue;
 font-size: 12px;
 -webkit-transform: translateY(-10px);
 transform: translateY(-10px);
 visibility: visible!important;
}
span {
    font-size: .8em;
    color: red;
}
span#characters {
    font-size: .8em;
    color: grey;
}
/* .buttonflex{
  border: solid black 1px;
} */
@media only screen and (max-width: 600px) {
    /* For mobile phones: */
    [class*="list__tile__title"] {
        font-size: 12px;
    }
    [class*="list__tile__sub-title"] {
        font-size: 9px;
    }
    [class*="connect"] {
        font-size: 12px;
    }
    [class*="ending"] {
        font-size: 12px;
    }
}
</style>
