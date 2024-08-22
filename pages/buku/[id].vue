<template>
    <div>
        <h2 class="text-start my-4">{{ buku.judul }}</h2>
        <div class="row">
            <div class="col-md-3">
                <div class="card">
                    <div class="card-body">
                        <span v-if="buku.cover"><img :src="buku.cover" :alt="buku.judul" class="cover"></span>
                        <span v-else><img
                                src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.svgrepo.com%2Fsvg%2F508699%2Flandscape-placeholder&psig=AOvVaw2-SWmfk33NzXubPfqn0P16&ust=1714794757874000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCNjln7nK8IUDFQAAAAAdAAAAABAE://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.svgrepo.com%2Fsvg%2F508699%2Flandscape-placeholder&psig=AOvVaw2-SWmfk33NzXubPfqn0P16&ust=1714794757874000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCNjln7nK8IUDFQAAAAAdAAAAABAE"></span>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-4 text-dark d-flek flek-column justify-contant-center">
                    <div class="list-group list-group-flush">
                        <h4>detail buku:</h4>
                        <h5>penulis: {{ buku.penulis }}</h5>
                        <h5>jumlah halaman: {{ buku.jumlah_halaman }}</h5>
                        <h5>tahun terbit: {{ buku.tahun_terbit }}</h5>
                        <h5>penerbit: {{ buku.penerbit }}</h5>
                    </div>
                    <div class="col-4 d-flex flex-column justify-content-center align-items">
                        <div class="mb-5">
                            <div class="card-body">
                                <img :src="buku.cover" class="ukuran center" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <NuxtLink to="/buku">
        <button type="submit" class="btn btn-lg rounded-5 px-5">kembali</button>
    </NuxtLink>
</template>

<script setup>

const supabase = useSupabaseClient()
const route = useRoute()
const buku = ref([])

const getBukuByID = async () => {
    const { data, error } = await supabase
        .from('buku')
        .select(`*, kategori_buku(*)`)
        .eq('id', route.params.id)
    if (data) buku.value = data[0]
}

onMounted(() => {
    getBukuByID()
})
</script>

<style scoped>
.cover {
    width: 100%;
}
</style>