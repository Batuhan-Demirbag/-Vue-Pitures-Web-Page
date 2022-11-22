<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/no-parsing-error -->
<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipeed flatting temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3">
        <v-icon class="mx-5" large>mdi-image</v-icon> 
      <v-toolbar-title class="align-center">
        <span class="title">Pictures Web</span>
                <!-- More tıklayınca en üstteki Pictures web kısmı -->
      </v-toolbar-title>
    </v-row>
    <v-list-item v-for="item in items" :key="item.icon" link>
      <!-- More tıklayınca her bir itemi arrey olarak al icon ve textini -->
      <v-list-item-action>
        <v-icon>{{item.icon}}</v-icon>
        </v-list-item-action>

        <v-list-item-content>
          <v-list-item-title>{{item.text}}</v-list-item-title>
        </v-list-item-content>

    </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!--HEADER TİTLE Design-->
    <v-app-bar app click-left>
      <!--app click-left (solda bir navigation ikonu)-->
      <v-app-bar-nav-icon @click="drawer=!drawer"/>
      <!--nav-iconuna tıkalayınca -->
      <v-icon class="mx-5" large>mdi-image</v-icon>
      <!--class="mx-5" (5 size space area)   mdi-video (ikonu geldi) -->
      <v-toolbar-title class="align-center">
        <!--Video Kod Title Design-->
        <span class="title">My Private Pictures Web App</span>
      </v-toolbar-title>
      <v-spacer />
      <!--boşluk bıraktı TİTLE'dan sonra-->
      <v-text-field
        class="mt-2"
        placeholder="Ara..."
        single-line
        append-icon="mdi-magnify"
        color="purple"
      /><!--Arama kısmı Design -->
      <v-spacer />
      <!--boşluk bıraktı ara...'dan sonra-->
      <v-btn class="ml-0" icon>
        <v-icon>mdi-apps</v-icon>
        <!--App button İconu -->
      </v-btn>
      <v-btn class="ma-2" icon>
        <v-icon>mdi-bell</v-icon>
        <!--Zil(bell) button İconu    class="ml-2"  2 boşluk-->
      </v-btn>
      <div>
        <v-menu
          v-model="menu"
          :close-on-content-click="false"
          :nudge-width="250"
          offset-x
          ><!--Menü  :close-on-content-click="false" tıklanınca gözükmesi | :nudge-width="250" boyutu  -->
          <template v-slot:activator="{ on }">
            <!--Slot tıklayınca "on" oluncak -->
            <v-avatar size="40">
              <img v-on="on" src="@/assets/github.png" />
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>Batuhan Demirbag</v-list-item-title>
                  <v-list-item-subtitle>Pictures Web</v-list-item-subtitle>
                  <!--GİTHUB RESMİNE TIKLAYINCA İSMİM VE ALT BAŞLIĞIM-->
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                  <!--GİTHUB RESMİNE TIKLAYINCA AYARLAR İKONU-->
                </v-list-item-action>
                <v-list-item-title>Ayarlar</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="purple"></v-switch>
                  <!--GİTHUB RESMİNE TIKLAYINCA Karanlık tema yapma -->
                </v-list-item-action>
                <v-list-item-title>Karanlık Tema</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary" text @click="menu = false">
                Çıkış Yap
              </v-btn>
              <!--GİTHUB RESMİNE TIKLAYINCA Çıkış yap kısmı -->
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-content>
      <!--İÇERİK KISMI -->
      <v-container>
        <v-row class="mb-4">
          <v-col sm="6" md="4" lg="3" xl="2" v-for="(item,index) in 100" :key="index">
            <v-card color="#D8BFD8">
              <!--İÇERİK KISMI 1-100 arasında https://picsum.photos daki imageler gelicek -->
              <v-img height="200px" :src="`https://picsum.photos/500/300?image=${(index+20)}`"/>
              <v-card-substitle class="number" style="font-weight: bold">Pictures {{item}}</v-card-substitle>
              <!--İÇERİK KISMI 1-100 arasında sayıları alarak -->
              <v-card-substitle class="text--primary"><div>Resim içeriği</div></v-card-substitle>
              <v-card-actions>
                <v-btn color="#800080" text>Kaydet</v-btn>
                <v-btn color="#800080" text>Paylaş</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
          
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    items: [
      { icon: "mdi-trending-up", text: "Popüler içerikler" },
      { icon: "mdi-youtube", text: "Youtube" },
      { icon: "mdi-history", text: "Geçmiş" },
      { icon: "mdi-playlist-play", text: "Playlistler" },
      { icon: "mdi-clock", text: "Önceden Bakılanlar" },
    ],
    drawer: false,
    menu: false,
    theme: true,
  }),
  watch: {
    theme: function (next) {
      this.$vuetify.theme.dark = next;
    },
  },
};
</script>
