<template>
  <v-app>
    <div>
    <v-container fluid class="pa-0">
      <v-layout row wrap class="lay pa-0">
        <v-flex xs2 offset-xs1 class="flex">
          <v-list>
            <v-list-tile v-for="info in footerInfos1" :key="info">
              <v-list-tile-content>
                <v-list-tile-title>
                  <span>{{ info.title }}</span>
                </v-list-tile-title>
                <v-list-tile-action-text>
                  <span>{{ info.children }}</span>
                </v-list-tile-action-text>
              </v-list-tile-content>
            </v-list-tile>
          </v-list>
        </v-flex>

        <v-flex xs2 offset-xs1 class="flex">
          <v-list>
            <v-list-tile v-for="info in footerInfos2" :key="info">
              <v-list-tile-content>
                <v-list-tile-title>
                  <span>{{ info.title }}</span>
                </v-list-tile-title>
                <v-list-tile-action-text>
                  <span>{{ info.children }}</span>
                </v-list-tile-action-text>
              </v-list-tile-content>
            </v-list-tile>
          </v-list>
        </v-flex>

        <v-flex xs2 offset-xs1 class="flex">
          <v-list>
            <v-list-tile v-for="info in footerInfos3" :key="info">
              <v-list-tile-content>
                <v-list-tile-title>
                  <span>{{ info.title }}</span>
                </v-list-tile-title>
                <v-list-tile-action-text>
                  <span>{{ info.children }}</span>
                </v-list-tile-action-text>
              </v-list-tile-content>
            </v-list-tile>
          </v-list>
        </v-flex>

        <v-flex xs2 class="flex">
          <v-list>
            <v-list-tile v-for="info in footerInfos4" :key="info">
              <v-list-tile-content>
                <v-list-tile-title>
                  <span>{{ info.title }}</span>
                </v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
          </v-list>
          <v-flex xs12 offset-xs1 id="subscribe">
            <v-text-field v-model="email" label="EMAIL" :rules="emailRules">
            </v-text-field>
            <v-flex>
              <v-btn depressed small id="button">SUBSCRIBE</v-btn>
            </v-flex>
          </v-flex>  
        </v-flex>
      </v-layout>
    </v-container>

    <v-container fluid class="pa-0">
      <v-layout row wrap class="lay">
        <v-flex xs12 class="text-xs-center connect" style="padding-top: 12px;">
          <span>Please Connect With Us</span>  
        </v-flex>
        <v-flex xs8 offset-xs2 color="grey lighten-1" style="padding-top: 10px; padding-bottom: 5px">
          <v-btn v-for="icon in icons" :key="icon" icon class="mx-5">
            <v-icon size="16px">{{ icon }}</v-icon>
          </v-btn>
        </v-flex>
      </v-layout>
    </v-container>

    <v-container fluid class="pa-0">
      <v-layout row wrap class="lay">
        <v-flex class="text-xs-center" style="padding-top: 10px; padding-bottom: 5px">
          &copy;2018 — <strong>SkyLim InfoTech Pvt. Ltd. </strong>
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
      emailRules: [
        v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
      ],
      footerInfos1:[
        {title:'POLICY INFO'}, {children:'Privacy Policy'}, {children:'Terms Of Sales'}, {children:'Terms Of Use'}, {children:'Report Abuse and TakeDown Policy'},
      ],
      footerInfos2:[
        {title:'COMPANY'}, {children:'About Us'}, {children:'Core Values'}, {children:'Blogs'}, {children:'Careers'}, {children:'SiteMap'},
      ],
      footerInfos3:[
        {title:'NEED HELP'}, {children:'FAQ'}, {children:'Contact Us'},        
      ],
      footerInfos4:[
        {title:'SUBSCRIBE'}
      ],
      icons: ['fab fa-facebook', 'fab fa-twitter', 'fas fa-at', 'fab fa-linkedin', 'fab fa-instagram', 'fab fa-whatsapp'],
    })
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.lay{
  border: solid black 1px;
  font-family: 'Open Sans', arial, Verdana, Tahoma, sans-serif;
  border: solid lightgray 1px;
}
.connect span{
  font-size: 16px;
}
#button{
  border-radius: 6px;
  border: solid 2px deepskyblue;
  color: deepskyblue;
  background-color: white;
}
#button:hover{
  color: white;
  background-color: deepskyblue;
}
</style>
