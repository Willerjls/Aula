<template>
  <q-page>
    <div class="q-pa-md">
      <div class="q-gutter-md">
        <q-input outlined v-model="codigo" label="Código" />
      </div>
      <div class="q-gutter-md q-pt-md">
        <q-input outlined v-model="nome" label="Nome do Produto" />
      </div>
      <div class="q-pa-md q-gutter-sm">
        <q-btn
          color="primary"
          icon="mail"
          label="Adicionar"
          @click="adicionar()"
        />
      </div>
      <div class="q-pa-md">
        <q-list bordered>
          <q-item
            clickable
            v-ripple
            v-for="(item, index) in lista"
            :key="item.codigo"
          >
            <q-item-section avatar>
              <q-avatar color="primary" text-color="white">
                {{ index }}
              </q-avatar>
            </q-item-section>
            <q-item-section>{{ item.codigo }} - {{ item.nome }}</q-item-section>
          </q-item>
        </q-list>
      </div>
    </div>
  </q-page>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "PageIndex",
  data() {
    return {
      codigo: "",
      nome: "",
    };
  },
  methods: {
    ...mapActions('lista', ['adicionarItem']),
    adicionar() {
      this.adicionarItem({ codigo: this.codigo, nome: this.nome });
      this.codigo = "";
      this.nome = "";
    },
  },
  computed: {
    ...mapGetters("lista", ["lista"]),
  },
};
</script>
