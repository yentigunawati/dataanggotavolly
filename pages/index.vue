<template>
  <div>
    <h1>dataanggotavolly</h1>
    <Nuxt-link to="/tambah"> isi data </Nuxt-link>
    <table border="1" width="50%">
      <thead>
        <tr>
          <th>no         </th>
          <th>nama</th>
          <th>kelas</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(visitor, index) in datas" :key="visitor.id">
          <td>{{ index + 1 }}</td>
          <td>{{ visitor.nama }}</td>
          <td>{{ visitor.kelas }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const supabase = useSupabaseAuthClient();
const datas = ref();

async function getData() {
  const { data, error } = await supabase.from("dataanggotavolly").select();
  datas.value = data;
}

onMounted(() => {
  getData();
});
</script>