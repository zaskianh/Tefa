<template>
    <div classs="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/pengunjung/tambah">
                    <div class="card bg-pengunjung rounded-5">
                        <div class="card-body">
                            <h2>pengunjung</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>  
            
            <div class="col-lg-6">
                <nuxt-link to="/buku/">
                    <div class="card bg-buku rounded-5">
                        <div class="card-body">
                            <h2>Cari Buku</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
    </div>
    <h2 style ="margin : 30px;"> <strong>STATISTIK</strong></h2>
    <div class="container-fluid">
<div class="row justify-content-evenly rounded-5">
    <div class="col-5">
    </div>
</div>
<div class="container-fluid">
<div class="row my-5 d-flex justify-content-around-5">
<div class="col-lg-6">
    <div class="card rounded-5 color1">
        <div class="card-body d-flex justify-content-around d-flex align-items-center">
        <h2 class="text">50 pengunjung</h2>
        </div>
        </div>
    </div>
    <div class="col-lg-6">
        <div class="card rounded-5 color2 ">
        <div class="card-body d-flex justify-content-around d-flex align-items-center">
            <h2 class="text">60 Buku</h2>
        </div>
        </div>
    </div>
    </div>
</div>
</div>
</template>


<style scoped>
.card {
    height: 250px;
    box-shadow: 1px 1px 10px #4653c7
}
.card.bg-pengunjung {
    background-image: url("/assets/img/bg-home-kunjungan.webp");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
.card.bg-buku {
    background: url("/assets/img/bg-home-cari-buku.webp");
    background-repeat: no-repeat; 
    background-position: center center; 
    background-size: cover;
}
</style>