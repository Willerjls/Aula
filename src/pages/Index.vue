<template>
  <q-page>
    <div class="q-pa-md">
      <div class="q-gutter-md">
        <q-input outlined v-model="produto" label="Produto" />
      </div>
      <div class="q-pa-md q-gutter-md">
        <q-btn color="primary" icon="mail" label="Adicionar" @click="adicionar()"/>
      </div>
      <div class="q-pa-md">
        <q-list bordered>
          <q-item clickable v-ripple v-for="(item, index) in lista" :key="index">
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white">
               {{ index }}
              </q-avatar>
            </q-item-section>
            <q-item-section>{{ item }}</q-item-section>
          </q-item>
        </q-list>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data(){
    return{
      produto: '',
      lista: ['Chocolate', 'Batata']
    }
  },
  methods:{
    adicionar(){
      this.lista.push(this.produto)
    }
  }
};
</script>
