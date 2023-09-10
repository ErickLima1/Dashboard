<template>
  <v-app theme=dark>
    <side-bar></side-bar>
    <v-main>
      <v-container>
        <h1 class="mb-4">Dashboard</h1>

        <v-card flat class="border mb-4">
          <div class="d-flex justify-space-between">
            <v-card-title>Ultimos Usuários</v-card-title>
            <v-card-title>
              <v-btn @click="isDialogOpen = true" variant="tonal" size="small">Adicionar</v-btn>

              <v-dialog v-model="isDialogOpen" width="600px">
                <v-card>
                  <v-card-title>Adicionar Usuário</v-card-title>
                  <v-card-text>
                    <v-row>
                      <v-col>
                        <v-text-field label="Nome" variant="outlined" :rules="emailRules"></v-text-field>
                      </v-col>

                      <v-col>
                        <v-text-field label="Email" variant="outlined" :rules="emailRules"></v-text-field>
                      </v-col>
                    </v-row>
                    <v-select label="Cargo" variant="outlined" :items="['Admin', 'Gerente', 'Convidado']">

                    </v-select>

                    <v-card-actions>
                      <v-spacer></v-spacer>
                      <v-btn variant="tonal" @click="isDialogOpen = false">Cancelar</v-btn>
                      <v-btn variant="tonal" color="success">Salvar</v-btn>
                    </v-card-actions>
                  </v-card-text>
                </v-card>
              </v-dialog>

            </v-card-title>
          </div>

          <v-table>
            <thead>
              <tr>
                <th>Nome</th>
                <th>Email</th>
                <th>Cargo</th>
                <th>Ação</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Erick</td>
                <td>Erick@gmail.com</td>
                <td><v-chip color="primary" variant="outlined">Administrador</v-chip></td>
                <td>
                  <v-btn variant="tonal" color="primary">Editar</v-btn>
                </td>
              </tr>
              <tr>
                <td>Costa</td>
                <td>Costa@outlook.com</td>
                <td><v-chip color="success" variant="outlined">Gerente</v-chip></td>
                <td>
                  <v-btn variant="tonal" color="primary">Editar</v-btn>
                </td>
              </tr>
            </tbody>
          </v-table>
        </v-card>
        
        <comp-card></comp-card>

      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';
import sideBar from './components/sideBar.vue';
import compCard from './components/compCard.vue';
// const isDrawerOpen = ref(false);
const isDialogOpen = ref(false);


const requeiredRule = value => {
  return !!value || 'Campo em Branco';
};

const emailFormatRule = value => {
  return value.includes('@') || 'Necessario Usar o @';
};

const emailRules = [requeiredRule, emailFormatRule];
</script>
