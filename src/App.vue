<template>
  <v-app>
    <v-navigation-drawer v-model="isDrawerOpen">
   <v-list>
   <v-list-subheader>Menu</v-list-subheader>
   <v-list-item prepend-icon="mdi-home">Home</v-list-item>
   <v-list-item prepend-icon="mdi-account">Usuários</v-list-item>

   <v-list-group value="Clientes">
        <template v-slot:activator="{ props }">
          <v-list-item
            v-bind="props"
            prepend-icon="mdi-account-circle"
            title="Clientes"
          ></v-list-item>
        </template>
        <v-list-item prepend-icon="mdi-currency-usd">Vendas</v-list-item>
        <v-list-item prepend-icon="mdi-chart-line" >Relatório</v-list-item>
   </v-list-group>
   
   </v-list>
  </v-navigation-drawer>

    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen"></v-app-bar-nav-icon>
      <v-app-bar-title>Meu App</v-app-bar-title>  
        <template #append>
          <v-btn icon class="mr-2">
              <v-badge dot color="info">
                <v-icon icon="mdi-bell-outline"></v-icon>
              </v-badge>
          </v-btn>
          <v-menu>
            <template #activator="{ props }">
              <v-avatar v-bind="props">
                <v-img
                cover
                src="https://cdn.vuetifyjs.com/images/john.jpg"
              ></v-img>
             </v-avatar>
            </template>
            <v-card min-width="200px">
              <v-list :lines="false" density="compact" nav>
                <v-list-item prepend-icon="mdi-account-outline">
                  <v-list-item-title >Meu Perfil</v-list-item-title>
                </v-list-item>
                <v-list-item prepend-icon="mdi-heart-outline">
                  <v-list-item-title >Favoritos</v-list-item-title>
                </v-list-item>
              
              </v-list>
            </v-card>

          </v-menu>

         
        </template>

    </v-app-bar>
    <v-main>
      <v-container>
        
        <h1 class="mb-6" v-ripple >Dashboard</h1>
       
            <v-card flat class="border mb-4">
              <div class="d-flex justify-space-between">
                <v-card-title>Últimos usuários</v-card-title>
               
                  <v-btn @click="isDialogOpen = true" variant="tonal" size="small" v-ripple>Adicionar Usuários</v-btn>
                  
                    
                    <v-dialog 
                  v-model="isDialogOpen"
                  width="600px"
                  class="custom-dialog">
                  <v-card>
                    <v-card-title>Adicionar Usuário</v-card-title>
                   <v-card-text>
                    <v-row>
                      <v-col>
                        <v-text-field label="Nome" variant="outlined"></v-text-field>
                      </v-col>
                      <v-col>
                        <v-text-field 
                        label="Email" 
                        variant="outlined"
                        :rules="emailRules"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                    <v-select 
                    label="Cargo" 
                    variant="outlined"
                    :items="['Desenvolvedor Master', 'Desenvolvedor Pleno', 'Analista de sistemas']"
                    ></v-select>
                  </v-card-text>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn variant="text" @click="isDialogOpen = false">Cancelar</v-btn>
                    <v-btn variant="tonal" color="success">Salvar</v-btn>
                  </v-card-actions>
                  </v-card>
                  </v-dialog>
              </div>
             
                <v-table density="compact">
                  <thead>
                    <tr>
                      <th>Nome</th>
                      <th>Email</th>
                      <th>Cargo</th>
                      <th>Ações</th>
                      

                    </tr>
                  </thead>
                <tbody>
                  <tr>
                    <td>Ícaro ao por do sol</td>
                    <td>icaro@gmail.com</td>
                    <td>
                      <v-chip color="primary" variant="outlined">Desenvolvedor Pleno</v-chip>
                    </td>
                    
                    <td>
                        <v-btn icon="mdi-pencil" variant="tonal" color="primary"></v-btn>                        
                      </td>
                  </tr>
                  <tr>
                    <td>Philipe Tigrão</td>
                    <td>Philipetigrao@gmail.com</td>
                    <td>
                      <v-chip color="secondary" variant="outlined">Desenvolvedor Master</v-chip>
                    </td>
                    <td>
                        <v-btn icon="mdi-pencil" variant="tonal" color="primary"></v-btn>
                      </td>
                  </tr> 
                  <tr>
                    <td>Nayron Vidal</td>
                    <td>nayronvidal@gmail.com</td>
                    <td>
                      <v-chip color="primary" variant="outlined">Desenvolvedor Pleno</v-chip>
                    </td>
                    <td>
                        <v-btn icon="mdi-pencil" variant="tonal" color="primary"></v-btn>
                      </td>
                  </tr>
                  <tr>
                    <td>Fabricia Kimberly</td>
                    <td>fkimberly@gmail.com</td>
                    <td>
                      <v-chip color="success" variant="outlined">Analista de sistemas</v-chip>
                    </td>
                    <td>
                        <v-btn icon="mdi-pencil" variant="tonal" color="primary"></v-btn>
                      </td>
                  </tr>
                  
                </tbody>
              </v-table>
            </v-card>
       

        <v-row>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card flat class="border">
              <v-img  
              class="aling-end text-white"
              :src="imageSrc"
              > 
                <v-card-title>Top 10 praias no Pará</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Salinas</v-card-subtitle>
           <v-card-text>
            <div>Atalaia</div>
            <div>Lorem ipsum dolor sit amet</div>
           </v-card-text>
           <v-card-actions>
            <v-btn variant="outlined" color="primary">Ver mais</v-btn>
            <v-btn prepend-icon="mdi-cart"variant="tonal" color="primary">Comprar</v-btn>
            
           </v-card-actions>
          </v-card>
        </v-col>

        <v-col cols="12" sm="6" md="4" lg="3">
          <v-card flat class="border">
              <v-img  
              class="aling-end text-white"
              :src="imageSrc"
              > 
                <v-card-title>Top 10 praias no Pará</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Algodoal</v-card-subtitle>
           <v-card-text>
            <div>Atalaia</div>
            <div>Lorem ipsum dolor sit amet</div>
           </v-card-text>
           <v-card-actions>
            <v-btn variant="outlined" color="primary">Ver mais</v-btn>
            <v-btn prepend-icon="mdi-cart"variant="tonal" color="primary">Comprar</v-btn>
           </v-card-actions>
          </v-card>
        </v-col>

        <v-col cols="12" sm="6" md="4" lg="3">
          <v-card flat class="border">
              <v-img  
              class="aling-end text-white"
              :src="imageSrc"
              > 
                <v-card-title>Top 10 praias no Pará</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Marudá</v-card-subtitle>
           <v-card-text>
            <div>Atalaia</div>
            <div>Lorem ipsum dolor sit amet</div>
           </v-card-text>
           <v-card-actions>
            <v-btn variant="outlined" color="primary">Ver mais</v-btn>
            <v-btn prepend-icon="mdi-cart"variant="tonal" color="primary">Comprar</v-btn>
           </v-card-actions>
          </v-card>
        </v-col>

        <v-col cols="12" sm="6" md="4" lg="3">
          <v-card flat class="border">
              <v-img  
              class="aling-end text-white"
              :src="imageSrc"
              > 
                <v-card-title>Top 10 praias no Pará</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3">Soure</v-card-subtitle>
           <v-card-text>
            <div>Atalaia</div>
            <div>Lorem ipsum dolor sit amet</div>
           </v-card-text>
           <v-card-actions>
            <v-btn variant="outlined" color="primary">Ver mais</v-btn>
            <v-btn prepend-icon="mdi-cart"variant="tonal" color="primary">Comprar</v-btn>
           </v-card-actions>
          </v-card>
        </v-col>
         
        </v-row>
      </v-container>
      <router-view />
    </v-main>
  </v-app>
</template>



<script>
import PraiaImage from '@/assets/salinas.jpg';
import { ref } from 'vue';

export default {
  setup() {
    // Variável reativa para controlar o estado do drawer
    
    const isDrawerOpen = ref(false);
    const isDialogOpen = ref(false);
    const emailRules = [
      value => {if (value) return true; 
         return 'O email é obirgatório'

      },
      value => {

        if(value.includes('@')){
          return true
        }

        return 'Email inválido'
      }
    ]

    return {
      isDrawerOpen, 
      isDialogOpen,
      emailRules,
      imageSrc: PraiaImage, 
    };
  },
  
};
</script>


