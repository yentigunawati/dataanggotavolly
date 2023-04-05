<template>
  <div>
    <h1>isi data anggota</h1>
    <form @submit.prevent="simpan">
    <input v-model="id" > <br/>
    <input v-model="nama" > <br/>
    <textarea v-model="kelas" placeholder="kelas"></textarea> <br/>
    <button type="submit">kirim</button>
    <Nuxt-link to="/">kembali</Nuxt-link>
    </form>
   </div>
</template>

<script setup>
const supabase= useSupabaseAuthClient()
const id= ref()
const nama= ref()
const kelas= ref()
async function simpan(){
await supabase
.from("dataangotavolly")
.insert({
  id: id.value,
  nama: nama.value,
  kelas: kelas.value,
})
const router= useRouter()
router.push("/tambah") 
}
{

}
</script>