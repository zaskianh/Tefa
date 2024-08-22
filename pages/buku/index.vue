<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-4">
                <h2 class="text-center my-4">buku</h2>
                <div class="my-3">
                    <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
                </div>
                <div class="my-3 text-muted">menampilkan 60 dari 60</div>
            </div>
        </div>
        <div class="row">
            <div class="col-lg-2" v-for="book in books" @click="navigateTo(`/buku/${book.id}`)">
                <div class="card mb-3 cover">
                    <div class="card-body">
                        <img :src="book.cover" class="novel" alt="novel1">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const books = ref([])
const keyword = ref('')

const getBuku = async () => {
    const { data, error } = await supabase
        .from("buku")
        .select(`*, kategori_buku(*)`)
        .order("id", { ascending: false })
        .ilike("judul", `%${keyword.value}%`);
    if (error) throw error
    if (data) books.value = data
}

onMounted(() => {
    getBuku()
})
</script>

<style scoped>
.card-body {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: 0 30;
    /* margin-right: 200px; */
    padding: 0;
}

img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: 0 30;

}
</style>
