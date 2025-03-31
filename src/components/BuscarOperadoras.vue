<template>
  <div class="max-w-2xl mx-auto mt-10 px-4">
    <h1 class="text-3xl font-bold text-center text-blue-600 mb-6">Buscar Operadoras</h1>

    <!-- Filtros -->
    <div class="flex flex-col md:flex-row gap-2 mb-6">
      <input
        v-model="termo"
        @keyup.enter="buscar"
        placeholder="Buscar por nome, CNPJ, modalidade..."
        class="flex-1 p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
      />

      <select
        v-model="uf"
        class="w-28 p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
      >
        <option value="">UF</option>
        <option v-for="estado in ufs" :key="estado" :value="estado">{{ estado }}</option>
      </select>

      <input
        v-model="cidade"
        placeholder="Cidade"
        class="flex-1 p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
      />

      <button
        @click="buscar"
        class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition"
      >
        Buscar
      </button>
    </div>

    <!-- Resultados -->
    <div v-if="operadorasPaginadas.length">
      <h2 class="text-xl font-semibold mb-4">Resultados:</h2>
      <ul class="space-y-4">
        <li
          v-for="op in operadorasPaginadas"
          :key="op.registroAns"
          class="p-4 border border-gray-200 rounded-lg shadow-sm hover:shadow-md transition"
        >
          <h3 class="text-lg font-bold text-blue-700">{{ op.nomeFantasia }}</h3>
          <p class="text-sm text-gray-700">{{ op.razaoSocial }} – {{ op.modalidade }}</p>
          <p class="text-sm text-gray-600">{{ op.cidade }}/{{ op.uf }} – Tel: ({{ op.ddd }}) {{ op.telefone }}</p>
        </li>
      </ul>

      <!-- Paginação -->
      <div class="flex justify-between mt-6">
        <button
          @click="voltarPagina"
          class="bg-gray-300 hover:bg-gray-400 px-4 py-2 rounded"
          :disabled="paginaAtual === 1"
        >
          ← Anterior
        </button>
        <span class="text-sm text-gray-600 self-center">Página {{ paginaAtual }}</span>
        <button
          @click="avancarPagina"
          class="bg-gray-300 hover:bg-gray-400 px-4 py-2 rounded"
          :disabled="paginaAtual * porPagina >= todasOperadoras.length"
        >
          Próxima →
        </button>
      </div>
    </div>

    <!-- Sem resultados -->
    <div v-else-if="buscou" class="text-center text-gray-500 mt-6">
      Nenhum resultado encontrado.
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      termo: '',
      uf: '',
      cidade: '',
      ufs: ['AC', 'AL', 'AM', 'AP', 'BA', 'CE', 'DF', 'ES', 'GO', 'MA',
            'MT', 'MS', 'MG', 'PA', 'PB', 'PR', 'PE', 'PI', 'RJ', 'RN',
            'RS', 'RO', 'RR', 'SC', 'SE', 'SP', 'TO'],
      todasOperadoras: [],
      operadorasPaginadas: [],
      buscou: false,
      paginaAtual: 1,
      porPagina: 10,
    };
  },
  methods: {
    async buscar() {
      try {
        const params = new URLSearchParams();
        if (this.termo) params.append("termo", this.termo);
        if (this.cidade) params.append("cidade", this.cidade);
        if (this.uf) params.append("uf", this.uf);

        const response = await fetch(`http://localhost:8080/operadoras/busca?${params.toString()}`);
        const data = await response.json();
        this.todasOperadoras = data;
        this.paginaAtual = 1;
        this.paginarResultados();
      } catch (err) {
        console.error("Erro ao buscar:", err);
        this.todasOperadoras = [];
      }
      this.buscou = true;
    },
    paginarResultados() {
      const inicio = (this.paginaAtual - 1) * this.porPagina;
      const fim = inicio + this.porPagina;
      this.operadorasPaginadas = this.todasOperadoras.slice(inicio, fim);
    },
    avancarPagina() {
      if ((this.paginaAtual * this.porPagina) < this.todasOperadoras.length) {
        this.paginaAtual++;
        this.paginarResultados();
      }
    },
    voltarPagina() {
      if (this.paginaAtual > 1) {
        this.paginaAtual--;
        this.paginarResultados();
      }
    }
  }
};
</script>

<style scoped>
/* Pode adicionar estilos extras aqui, mas Tailwind já cobre tudo */
</style>
