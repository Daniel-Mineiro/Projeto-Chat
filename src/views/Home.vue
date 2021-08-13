<template>
  <v-app>
    <v-container fluid>
      <v-row>
        <v-col cols="12" sm="3">
          <v-list-item>
            <v-app-bar id="Perfil" flat>
              <v-badge
                bordered
                bottom
                color="green"
                dot
                offset-x="22"
                offset-y="26"
              >
                <v-list-item-avatar class="ml-0 mb-3" size="40">
                  <v-img src="../assets/Daniel.jpeg"></v-img>
                </v-list-item-avatar>
              </v-badge>

              <v-list-item-title class="title pl-0 ml-2 mt-n3">
                Daniel Mineiro</v-list-item-title
              >
            </v-app-bar>
          </v-list-item>

          <v-app-bar id="busca" class="mt-8" flat color="rgba(0,0,0,0)">
            <v-text-field
              rounded
              solo
              label="Busque aqui"
              append-icon="mdi-magnify"
            ></v-text-field>
          </v-app-bar>

          <v-list id="contatos" two-line>
            <v-list-item-group active-class="grey" multiple>
              <template v-for="(item, index) in items">
                <v-list-item :key="item.title">
                  <v-badge
                    bordered
                    bottom
                    color="green"
                    dot
                    offset-x="22"
                    offset-y="26"
                  >
                    <v-list-item-avatar>
                      <v-img :src="item.avatar"></v-img>
                    </v-list-item-avatar>
                  </v-badge>
                  <template>
                    <v-list-item-content>
                      <v-list-item-title
                        v-text="item.title"
                      ></v-list-item-title>

                      <v-list-item-subtitle
                        v-text="item.subtitle"
                      ></v-list-item-subtitle>
                      
                      
                    </v-list-item-content>
                  </template>
                </v-list-item>

                <v-divider
                  v-if="index < items.length - 1"
                  :key="index"
                ></v-divider>
              </template>
            </v-list-item-group>
          </v-list>
        </v-col>
        <v-col cols="12" sm="9">
          <v-app-bar id="pessoa1" flat>
            <v-avatar class="mt-n1" size="40" elevation="10">
              <v-img src="../assets/Maria-Laura.jpg"></v-img>
            </v-avatar>

            <div class="text-center">
              <v-bottom-sheet v-model="sheet" persistent>
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                    :disabled="loading"
                    class="title pl-0 ml-2 mt-n4"
                    color="black"
                    plain
                    text
                  >
                    <v-title class="title pl-0 ml-2 mt-1">
                      Maria Laura
                    </v-title>
                  </v-btn>
                </template>
                <v-sheet id="Inf">
                  <v-btn
                    class="mt-6"
                    text
                    color="error"
                    @click="sheet = !sheet"
                  >
                    <v-icon>close</v-icon>
                  </v-btn>
                  <v-row>
                    <v-col cols="12" sm="12">
                      <v-expansion-panels v-model="panel" multiple>
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-expansion-panel id="select">
                              <v-expansion-panel-header>
                                <h3>Informações Pessoias</h3>
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <v-card>
                                  <v-avatar class="ml-2 mb-1" size="60">
                                    <v-img
                                      src="../assets/Maria-Laura.jpg"
                                    ></v-img>
                                  </v-avatar>
                                  <v-subtitle class="pl-15 ml-n1 mt-n8">
                                    RD Station
                                    <v-icon>check</v-icon></v-subtitle
                                  >
                                  <v-select
                                    :items="items1"
                                    label="Lead"
                                    solo
                                    class="pl-15 ml-16 mr-8 mt-n4"
                                  ></v-select>

                                  <v-card-title class="title pl-0 ml-2 mt-n4"
                                    >Maria Laura</v-card-title
                                  >
                                  <v-card-subtitle class="pl-0 ml-2 mt-n5"
                                    >(61) 9 9999-9999</v-card-subtitle
                                  >
                                  <v-card-subtitle class="pl-0 ml-2 mt-n8"
                                    >maria_Laura@gmail.com</v-card-subtitle
                                  >
                                  <v-card-subtitle class="pl-0 ml-1 mt-n8"
                                    ><v-icon>mdi-instagram</v-icon>
                                    Maria_Laura</v-card-subtitle
                                  >
                                </v-card>
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-expansion-panel id="select">
                              <v-expansion-panel-header>
                                <h3>Imagens</h3>
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <div class="mb-4">
                                  <v-avatar size="70" tile class="mr-3">
                                    <v-img
                                      src="../assets/paisagem1.jpg"
                                    ></v-img>
                                  </v-avatar>
                                  <v-avatar size="70" tile class="mr-3">
                                    <v-img
                                      src="../assets/paisagem2.jpg"
                                    ></v-img>
                                  </v-avatar>
                                </div>
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-expansion-panel id="select">
                              <v-expansion-panel-header>
                                <h3>Arquivos</h3>
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                Não há arquivo
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                          </v-col>
                        </v-row>
                        <v-expansion-panel id="select"> </v-expansion-panel>
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-expansion-panel id="select">
                              <v-expansion-panel-header>
                                <h3>Tags</h3>
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <v-combobox
                                  v-model="chips"
                                  :items="items2"
                                  chips
                                  clearable
                                  label=""
                                  multiple
                                  prepend-icon="mdi-filter-variant"
                                  solo
                                >
                                  <template
                                    v-slot:selection="{
                                      attrs,
                                      item,
                                      select,
                                      selected,
                                    }"
                                  >
                                    <v-chip
                                      v-bind="attrs"
                                      :input-value="selected"
                                      close
                                      @click="select"
                                      @click:close="remove(item)"
                                    >
                                      <strong>{{ item }}</strong
                                      >;
                                      <span>(indeterminado)</span>
                                    </v-chip>
                                  </template>
                                </v-combobox>
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-expansion-panel id="select">
                              <v-expansion-panel-header>
                                <h3>Bloco de Notas</h3>
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <v-app-bar color="rgba(0,0,0,0)" flat>
                                  <v-text-field
                                    v-model="message"
                                    filled
                                    clear-icon="mdi-close"
                                    label="Escreva aqui..."
                                    type="text"
                                    @click:clear="clearMessage"
                                  ></v-text-field>
                                </v-app-bar>
                                <v-card-text>
                                  <v-chip @click="lights">
                                    <v-icon center> mdi-send </v-icon></v-chip
                                  ></v-card-text
                                >
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-expansion-panel id="select">
                              <v-expansion-panel-header>
                                <h3>Histórico de conversas</h3>
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                Não há conversas antigas
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                          </v-col>
                        </v-row>
                      </v-expansion-panels>
                    </v-col>
                  </v-row>
                </v-sheet>
              </v-bottom-sheet>
            </div>

            <v-spacer></v-spacer>

            <v-divider vertical inset class="mt-1"></v-divider>
            <v-btn color="black" icon class="mt-n2">
              <v-icon>phone</v-icon>
            </v-btn>
          </v-app-bar>
          <div id="Home" class="mt-3">
            <v-app-bar color="rgba(0,0,0,0)" flat class="mb-16">
              <v-spacer></v-spacer>
              <v-card id="card1" class="mt-10 mr-2" max-width="350px">
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="mb-4">Olá,tudo bem?</div>
                    <v-list-item-subtitle>Enviado 13:03</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-app-bar>
            <v-app-bar color="rgba(0,0,0,0)" flat class="mb-16">
              <v-card id="card2" class="mt-10" max-width="350px">
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="mb-4">
                      Oi, tudo bem sim. Poderia me mandar as fotos, por favor?
                    </div>
                    <v-list-item-subtitle>Enviado 13:15</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-app-bar>

            <v-app-bar color="rgba(0,0,0,0)" flat class="mb-16">
              <v-spacer></v-spacer>

              <v-card id="card1" class="mt-10 mr-2" max-width="350px">
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="mb-4">
                      <v-avatar size="70" tile class="mr-3">
                        <v-img src="../assets/paisagem1.jpg"></v-img>
                      </v-avatar>
                      <v-avatar size="70" tile class="mr-3">
                        <v-img src="../assets/paisagem2.jpg"></v-img>
                      </v-avatar>
                    </div>

                    <v-list-item-subtitle>Enviado 13:23</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-app-bar>
            <v-app-bar color="rgba(0,0,0,0)" flat class="mb-8">
              <v-spacer></v-spacer>
              <v-card id="card1" class="mt-10 mr-2" max-width="350px">
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="mb-4">As fotos estão acima!!</div>
                    <v-list-item-subtitle>Enviado 13:23</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-app-bar>
            <v-app-bar color="rgba(0,0,0,0)" flat class="mb-16">
              <v-card id="card2" class="mt-10 mr-2" max-width="350px">
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="mb-4">Belas fotos, parabéns!</div>
                    <v-list-item-subtitle>Enviado 13:24</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-app-bar>
            <div id="teclado">
              <v-app-bar id="teclado" class="mt-5" color="rgba(0,0,0,0)" flat>
                <v-text-field
                  v-model="message"
                  :append-outer-icon="message ? 'mdi-send' : 'mdi-microphone'"
                  rounded
                  solo
                  clear-icon="mdi-close"
                  clearable
                  label="Escreva aqui..."
                  type="text"
                  @click:append-outer="sendMessage"
                  @click:clear="clearMessage"
                ></v-text-field>
              </v-app-bar>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>
<script>
import foto1 from "../assets/Maria-Laura.jpg";
import foto2 from "../assets/Felipe.jpg";
import foto3 from "../assets/chico.jpg";

export default {
  data: () => ({
    selected: [0],
    items: [
      {
        avatar: foto1,
        subtitle: " Belas fotos, parabéns!",
        title: "Maria Laura",
      },
      {
        avatar: foto2,
        subtitle: "Até breve!!",
        title: "Felipe",
      },
      {
        avatar: foto3,
        subtitle: "OK, vamos sim",
        title: "Chico",
      },
    ],
    panel: [0],

    password: "Password",
    show: false,
    message: "",
    marker: true,
    iconIndex: 0,

    sheet: false,
    items1: ["Lead", "Cliente", "Outro", "Spam"],

    chips: ["Desenvolvedor", "CTO"],
    items2: ["Vendedora", "Auxiliar Amdinistrativo", "Desenvolvedor", "CTO"],
  }),
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? "dark" : "light";
    },
  },
  methods: {
    sendMessage() {
      this.resetIcon();
      this.clearMessage();
    },
    clearMessage() {
      this.message = "";
    },
    resetIcon() {
      this.iconIndex = 0;
    },
    remove(item) {
      this.chips.splice(this.chips.indexOf(item), 1);
      this.chips = [...this.chips];
    },

    lights() {
      this.clearMessage();
      alert("Sua anotação foi guardada com sucesso...");
    },
  },
};
</script>
<style >
#Inf {
  padding: 5px;
  background-color: #eefbff;
}
#Perfil {
  background-color: #e4e2e2;
  border-radius: 5px;
}
#contatos {
  background-color: #e4e2e2;
  border-radius: 5px;
}
#pessoa1 {
  background-color: #e4e2e2;
  border-radius: 5px;
}
#Home {
  background-color: #c4e9f5;
  border-radius: 5px;
}
#card1 {
  background-color: #67b1fc;
}
#card2 {
  background-color: #f8f8ff;
}
#teclado {
  background-color: #f8f8ff;
}
#select {
  background-color: #e7e7e7;
}
</style>
