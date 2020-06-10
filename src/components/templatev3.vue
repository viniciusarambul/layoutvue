<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      color="#013370"
      dark
    >
    <v-list >
      
      <v-list-item link>
       <v-list-item-content>
         <v-list-item-title class="title">Vinicius Arambul</v-list-item-title>
         <v-list-item-subtitle>ti@wdobrasil.com.br</v-list-item-subtitle>
       </v-list-item-content>

       <v-list-item-action>
         <v-icon>mdi-menu-down</v-icon>
       </v-list-item-action>
     </v-list-item>
   </v-list>
    <v-list>
    <v-list-item link>
      <v-list-item-icon>
        <v-icon>mdi-home</v-icon>
      </v-list-item-icon>

      <v-list-item-title>Home</v-list-item-title>
    </v-list-item>
    <v-list-group
      prepend-icon="mdi-calendar"
    >
      <template v-slot:activator>
        <v-list-item-title>Agendas</v-list-item-title>
      </template>
        <v-list-item style="padding-left: 35px !important;"
          v-for="(agenda, i) in agendas"
          :key="i"
          link
        >
          <v-list-item-title  v-text="agenda[0]"></v-list-item-title>
          
        </v-list-item>
      </v-list-group>
      
      <v-list-group
        prepend-icon="mdi-calendar"
      >
        <template v-slot:activator>
          <v-list-item-title>BSC</v-list-item-title>
        </template>
          <v-list-item style="padding-left: 35px !important;"
            v-for="(bsc, i) in bscs"
            :key="i"
            link
          >
            <v-list-item-title  v-text="bsc[0]"></v-list-item-title>
            
          </v-list-item>
        </v-list-group>
    <v-list-group
      prepend-icon="mdi-chart-line"
    >
      <template v-slot:activator>
        <v-list-item-title>Relatórios</v-list-item-title>
      </template>

      <v-list-group
        no-action
        sub-group
      >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Comercial</v-list-item-title>
          </v-list-item-content>
        </template>

        <v-list-item style="padding-left: 35px !important;"
          v-for="(relatorio, i) in relatorios"
          :key="i"
          link
        >
      
          <v-list-item-title  v-text="relatorio[0]"></v-list-item-title>
          
        </v-list-item>
      </v-list-group>

      <v-list-group
        sub-group
        no-action
      >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>Pedagógico</v-list-item-title>
          </v-list-item-content>
        </template>
          <v-list-item style="padding-left: 35px !important;"
          v-for="(pedagogico, i) in pedagogicos"
          :key="i"
        >
          <v-list-item-title v-text="pedagogico[0]"></v-list-item-title>
          <v-list-item-action>
            <v-icon v-text="pedagogico[1]"></v-icon>
          </v-list-item-action>
        </v-list-item>
      </v-list-group>
    </v-list-group>
  </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="#013370"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>Aplicação</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
        
        </v-row>
      </v-container>
    </v-content>
    <!--<v-footer
      color="#013370"
      app
    >
      <span class="white--text">&copy; Washington Franchising 2020</span>
    </v-footer>-->
  </v-app>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: true,
      agendas: [
        ['Agenda Geral'],
      ],
      bscs: [
        ['Indicadores'],
        ['Sincronizar Dados'],
        ['Dashboards AWF'],
        ['Dashboards Unidade'],
      ],
      relatorios: [
        ['Matrículas por Período'],
        ['Necessidade de Matrícula'],
      ],
      pedagogicos: [
        ['Alunos Matrículados'],
        ['Geral de Notas'],
        ['Retenção'],
        ['Cancelamentos'],
      ],
    }),
  }
</script>