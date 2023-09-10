<template>
    <div>
        <v-navigation-drawer v-model="isDrawerOpen">
            <v-list>
                <v-list-subheader>Menu</v-list-subheader>
                <v-list-item prepend-icon="mdi-home">Home</v-list-item>
                <v-list-item prepend-icon="mdi-account">Usuários</v-list-item>
                
                <v-list-group value="Clientes">
                  <template #activator="{ props }">
                    <v-list-item 
                      v-bind="props"
                      prepend-icon="mdi-account-circle"
                      title="Clientes"
                      ></v-list-item>
                    </template>
                    <v-list-item prepend-icon="mdi-currency-usd">Vendas</v-list-item>
                    <v-list-item prepend-icon="mdi-chart-line">Relatorio</v-list-item>
                </v-list-group>
              </v-list>
        </v-navigation-drawer>
        
        <v-app-bar fiat class="border-b">
            <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen"></v-app-bar-nav-icon>
      <v-app-bar-title>Meu App</v-app-bar-title>

      <template #append>
        <v-btn icon class="mr-2">
          <v-badge dot color="info" :content="1">
            <v-icon icon="mdi-bell-outline"></v-icon>
          </v-badge>
        </v-btn>

        <v-menu>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img cover src="https://avatarfiles.alphacoders.com/334/thumb-334664.png"></v-img>
            </v-avatar>
          </template>
            <v-card min-width="200px">
                <v-list :lines="false" density="compact">
                    <v-list-item prepend-icon="mdi-account">
                        <v-btn>
                            <v-list-item>Perfil</v-list-item>
                        </v-btn>    
                    </v-list-item>
                </v-list>
                <v-list :lines="false" density="compact">
                    <v-list-item prepend-icon="mdi-exit-run">
                        <v-btn>
                            <v-list-item>Sair</v-list-item>
                        </v-btn>
                    </v-list-item>
            </v-list>
        </v-card>
        </v-menu>
        
      </template>
        </v-app-bar>
      </div>
    
  </template>

  <script>
  import { ref, watch, onMounted } from 'vue';
  
  export default {
    setup() {
      const isDrawerOpen = ref(false);
  
      return {
        isDrawerOpen,
      };
    },
  };
  </script>