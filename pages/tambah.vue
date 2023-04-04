<template>
  <div>
    <h3>tambah data</h3>
    <form @submit.prevent="addData">
      <div>
        <label for="">nama</label>
        <input type="text" v-model="nama" />
      </div>
      <div>
        <label for="">Kelas</label>
        <input type="number" v-model="kelas" />
      </div>
      <button type="submit">tambah</button>
    </form>
  </div>
</template>

<script setup>
const supabase = useSupabaseAuthClient();
const nama = ref();
const kelas = ref();
const addData = async () => {
  const { data, error } = await supabase.from("dataanggotavolly").insert({
    nama: nama.value,
    kelas: kelas.value,
  });
  alert("berhasil tambah data");
  navigateTo("/");
  if (error) {
    console.log(error);
  }
};
</script>
