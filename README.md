<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">

<title>MBG SMK Informatika CBI</title>

<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

<style>

body{
background:#f2f5f7;
font-family:Arial,Helvetica,sans-serif;
margin:0;
padding-bottom:80px;
}

.header{
background:#198754;
color:#fff;
padding:15px;
text-align:center;
font-size:22px;
font-weight:bold;
position:sticky;
top:0;
z-index:999;
}

.page{
display:none;
padding:15px;
}

.active{
display:block;
}

.card{
border-radius:15px;
margin-bottom:15px;
}

.item{
background:#fff;
padding:12px;
margin-top:10px;
border-radius:10px;
box-shadow:0 2px 5px rgba(0,0,0,.15);
}

.bottom{
position:fixed;
bottom:0;
left:0;
width:100%;
background:#fff;
display:flex;
justify-content:space-around;
padding:8px;
box-shadow:0 -2px 10px rgba(0,0,0,.15);
}

.bottom button{
background:none;
border:none;
font-size:13px;
font-weight:bold;
}

.stat{
font-size:24px;
font-weight:bold;
color:#198754;
}

</style>

</head>

<body>

<div class="header">
🍱 MBG SMK INFORMATIKA CBI
</div>

<!-- ================= DASHBOARD ================= -->

<div id="dashboard" class="page active">

<div class="card p-3">

<h4>Dashboard</h4>

<div class="item">
Total Pembagian
<div class="stat" id="totalPembagian">0</div>
</div>

<div class="item">
Total Ompreng
<div class="stat" id="totalOmpreng">0</div>
</div>

<div class="item">
Guru Hadir
<div class="stat" id="totalGuru">0</div>
</div>

</div>

</div>

<!-- ================= KELAS ================= -->

<div id="kelas" class="page">

<div class="card p-3">

<h4>Pembagian Kelas</h4>

<select id="kelasSelect" class="form-select">

<option>X PPLG 1</option>
<option>X PPLG 2</option>
<option>X PPLG 3</option>
<option>X PPLG 4</option>

<option>XI PPLG 1</option>
<option>XI PPLG 2</option>
<option>XI PPLG 3</option>
<option>XI PPLG 4</option>

<option>XII PPLG 1</option>
<option>XII PPLG 2</option>
<option>XII PPLG 3</option>
<option>XII PPLG 4</option>

<option>X DKV 1</option>
<option>X DKV 2</option>
<option>X DKV 3</option>
<option>X DKV 4</option>

<option>XI DKV 1</option>
<option>XI DKV 2</option>
<option>XI DKV 3</option>
<option>XI DKV 4</option>

<option>XII DKV 1</option>
<option>XII DKV 2</option>
<option>XII DKV 3</option>
<option>XII DKV 4</option>

<option>Gugus 1</option>
<option>Gugus 2</option>
<option>Gugus 3</option>
<option>Gugus 4</option>
<option>Gugus 5</option>
<option>Gugus 6</option>
<option>Gugus 7</option>
<option>Gugus 8</option>
<option>Gugus 9</option>

</select>

<br>

<input
type="number"
id="jumlahOmpreng"
class="form-control"
placeholder="Jumlah Ompreng">

<button
id="btnTambahKelas"
class="btn btn-success mt-3">

Simpan Pembagian

</button>

<hr>

<div id="listKelas"></div>

</div>

</div>
<div id="guru" class="page">

<div class="card p-3">

<h4>Guru Hadir</h4>

<input
type="text"
id="cariGuru"
class="form-control"
placeholder="Cari Guru">

<br>

<div id="daftarGuru"></div>

<button
id="btnSimpanGuru"
class="btn btn-success mt-3">

Simpan Guru Hadir

</button>

</div>

</div>

<!-- ================= PEMBAGIAN GURU ================= -->

<div id="bagiGuru" class="page">

<div class="card p-3">

<h4>Pembagian Guru / Tendik</h4>

<label>Sisa Ompreng</label>

<input
type="number"
id="sisaOmpreng"
class="form-control"
placeholder="Masukkan sisa ompreng">

<button
class="btn btn-success mt-3"
id="btnHitung">

Hitung Pembagian

</button>

<hr>

<div id="hasilPembagianGuru"></div>

</div>

</div>

<!-- ================= RIWAYAT ================= -->

<div id="riwayat" class="page">

<div class="card p-3">

<h4>Riwayat Pembagian</h4>

<div id="isiRiwayat"></div>

<button
class="btn btn-danger mt-3"
id="btnReset">

Reset Semua Data

</button>

</div>

</div>

<!-- ================= MENU ================= -->

<div class="bottom">

<button onclick="showPage('dashboard')">
🏠<br>Home
</button>

<button onclick="showPage('kelas')">
📦<br>Kelas
</button>

<button onclick="showPage('guru')">
👨‍🏫<br>Guru
</button>

<button onclick="showPage('bagiGuru')">
🍱<br>Bagi
</button>

<button onclick="showPage('riwayat')">
📋<br>Riwayat
</button>

</div>

<script>

const daftarGuru=[

"Adi Putra Pamungkas",
"Agus Hipni Apendi",
"Ai Rahmawati",
"Ananda Putri Sutarlan",
"Anis Sabuh",
"ARMAN SARI",
"Cepi Ismail",
"DEBI HERMAWAN",
"Dede Rohmat",
"DEDE SUTIYANAH",
"Dinda Safitri",
"Duduh Durahman",
"Ela Nurlaela",
"Endin Saepudin",
"Erdy Herdiawan",
"Firman Agiansyah",
"Haripan Oktapiana",
"Hendi Suhendi",
"Heru",
"ILHAM MAULANA",
"Ipda Sulastina",
"Ir. Ade Ruslan",
"Irma Maulani",
"Ismi Fajarina Isnaeni",
"Kiki Taskiyah",
"M. RAMADHANY PUTRA. R",
"M. Rifki Ilham Sani",
"MUHAMAD FIRMANSYAH",
"Muhamad Nurhamzah",
"MUHAMAD RIAN HIDAYAT",
"MUHAMMAD HENDRY KUSUMA",
"MUHAMMAD NAUFAL SAPHAN",
"Nanda Nadia Elisa",
"Neli Nur Ramdhani",
"Prida Kusuma",
"RAFLY KAEZA RAMADHAN",
"Ratna Suminar",
"Robi Mulya Gunawan",
"Rohman",
"Rohman Hidayat",
"Roni Gandi",
"Siska Ambarwaty Ramdhan",
"Siti Rohimah",
"SITI SARAH",
"TABAH SAPUTRA WIBISONO",
"Tuti Anggraeni",
"Widya Khaerul Bariyyah",
"Winda Sulastri"

];

let guruHadir=[];
let dataKelas=[];

function showPage(id){

document.querySelectorAll(".page").forEach(function(x){

x.classList.remove("active");

});

document.getElementById(id).classList.add("active");

}

function renderGuru(){

let hadir=JSON.parse(localStorage.getItem("guruHadir"))||[];

let html="";

daftarGuru.forEach(function(nama){

let cek=hadir.includes(nama)?"checked":"";

html+=`

<div class="form-check">

<input
type="checkbox"
class="form-check-input guruCheck"
value="${nama}"
${cek}>

<label class="form-check-label">

${nama}

</label>

</div>

`;

});

document.getElementById("daftarGuru").innerHTML=html;

}

// ================= SIMPAN GURU HADIR =================

document.getElementById("btnSimpanGuru").onclick=function(){

guruHadir=[];

document.querySelectorAll(".guruCheck").forEach(function(item){

if(item.checked){

guruHadir.push(item.value);

}

});

localStorage.setItem("guruHadir",JSON.stringify(guruHadir));

document.getElementById("totalGuru").innerHTML=guruHadir.length;

alert("Data guru hadir berhasil disimpan.");

}

// ================= CARI GURU (VERSI BARU) =================

document.getElementById("cariGuru").addEventListener("keyup",filterGuru);

function filterGuru(){

let cari=document.getElementById("cariGuru").value.toLowerCase();

let html="";

let hadir=JSON.parse(localStorage.getItem("guruHadir"))||[];

daftarGuru.forEach(function(nama){

if(nama.toLowerCase().includes(cari)){

let cek=hadir.includes(nama)?"checked":"";

html+=`

<div class="form-check">

<input
type="checkbox"
class="form-check-input guruCheck"
value="${nama}"
${cek}>

<label class="form-check-label">

${nama}

</label>

</div>

`;

}

});

document.getElementById("daftarGuru").innerHTML=html;

}

// ================= PEMBAGIAN KELAS =================

document.getElementById("btnTambahKelas").onclick=function(){

let kelas=document.getElementById("kelasSelect").value;
let jumlah=parseInt(document.getElementById("jumlahOmpreng").value);

if(isNaN(jumlah)||jumlah<=0){

alert("Masukkan jumlah ompreng.");

return;

}

let data=JSON.parse(localStorage.getItem("dataKelas"))||[];

data.push({

kelas:kelas,
jumlah:jumlah,
ambil:false,
kembali:false,
tanggal:new Date().toLocaleString()

});

localStorage.setItem("dataKelas",JSON.stringify(data));

document.getElementById("jumlahOmpreng").value="";

tampilKelas();

updateDashboard();

}

// ================= TAMPIL DATA KELAS =================

function tampilKelas(){

let data=JSON.parse(localStorage.getItem("dataKelas"))||[];

let html="";

data.forEach(function(item,index){

html+=`

<div class="item">

<b>${item.kelas}</b><br>

Ompreng : <b>${item.jumlah}</b><br>

<label>

<input
type="checkbox"
${item.ambil?"checked":""}
onchange="ubahAmbil(${index},this.checked)">

 Sudah Diambil

</label>

<br>

<label>

<input
type="checkbox"
${item.kembali?"checked":""}
onchange="ubahKembali(${index},this.checked)">

 Sudah Dikembalikan

</label>

</div>

`;

});

document.getElementById("listKelas").innerHTML=html;

}

// ================= CHECKLIST AMBIL =================

function ubahAmbil(index,status){

let data=JSON.parse(localStorage.getItem("dataKelas"))||[];

data[index].ambil=status;

localStorage.setItem("dataKelas",JSON.stringify(data));

}

// ================= CHECKLIST KEMBALI =================

function ubahKembali(index,status){

let data=JSON.parse(localStorage.getItem("dataKelas"))||[];

data[index].kembali=status;

localStorage.setItem("dataKelas",JSON.stringify(data));

}

// ================= DASHBOARD =================

function updateDashboard(){

let data=JSON.parse(localStorage.getItem("dataKelas"))||[];

let totalPembagian=data.length;

let totalOmpreng=0;

data.forEach(function(item){

totalOmpreng+=Number(item.jumlah);

});

document.getElementById("totalPembagian").innerHTML=totalPembagian;

document.getElementById("totalOmpreng").innerHTML=totalOmpreng;

let hadir=JSON.parse(localStorage.getItem("guruHadir"))||[];

document.getElementById("totalGuru").innerHTML=hadir.length;

}


// ================= LOAD AWAL =================

window.onload=function(){

// Load guru hadir
guruHadir=JSON.parse(localStorage.getItem("guruHadir"))||[];

// Tampilkan daftar guru
renderGuru();

// Tampilkan data kelas
tampilKelas();

// Tampilkan riwayat
tampilRiwayat();

// Update dashboard
updateDashboard();

}

// ================= HITUNG PEMBAGIAN GURU =================

document.getElementById("btnHitung").onclick=function(){

let sisa=parseInt(document.getElementById("sisaOmpreng").value);

if(isNaN(sisa)||sisa<=0){

alert("Masukkan jumlah sisa ompreng.");

return;

}

let hadir=JSON.parse(localStorage.getItem("guruHadir"))||[];

if(hadir.length==0){

alert("Belum ada guru yang hadir.");

return;

}

let jatah=Math.floor(sisa/hadir.length);

let sisaOmpreng=sisa%hadir.length;

let html="";

html+=`
<div class="alert alert-success">
<b>Guru Hadir :</b> ${hadir.length}<br>
<b>Jatah / Orang :</b> ${jatah}<br>
<b>Sisa Ompreng :</b> ${sisaOmpreng}
</div>
`;

hadir.forEach(function(nama,index){

html+=`

<div class="item">

<b>${index+1}. ${nama}</b>

<br><br>

<div class="form-check">

<input
class="form-check-input"
type="checkbox"
id="ambil${index}">

<label class="form-check-label">

Sudah Ambil

</label>

</div>

<div class="form-check">

<input
class="form-check-input"
type="checkbox"
id="kembali${index}">

<label class="form-check-label">

Sudah Kembali

</label>

</div>

</div>

`;

});

document.getElementById("hasilPembagianGuru").innerHTML=html;
simpanRiwayatGuru();

}

// ================= RESET DATA =================

document.getElementById("btnReset").onclick=function(){

if(!confirm("Yakin ingin menghapus semua data?")){
return;
}

localStorage.removeItem("dataKelas");
localStorage.removeItem("guruHadir");
localStorage.removeItem("riwayatGuru");

document.getElementById("hasilPembagianGuru").innerHTML="";
document.getElementById("isiRiwayat").innerHTML="";
document.getElementById("listKelas").innerHTML="";
document.getElementById("jumlahOmpreng").value="";
document.getElementById("sisaOmpreng").value="";

updateDashboard();
renderGuru();

alert("Semua data berhasil dihapus.");

}

// ================= SIMPAN RIWAYAT GURU =================

function simpanRiwayatGuru(){

let hadir=JSON.parse(localStorage.getItem("guruHadir"))||[];

let sisa=parseInt(document.getElementById("sisaOmpreng").value);

let jatah=Math.floor(sisa/hadir.length);

let data=JSON.parse(localStorage.getItem("riwayatGuru"))||[];

data.unshift({

tanggal:new Date().toLocaleString(),

guru:hadir.length,

ompreng:sisa,

jatah:jatah

});

localStorage.setItem("riwayatGuru",JSON.stringify(data));

tampilRiwayat();

}

// ================= TAMPIL RIWAYAT =================

function tampilRiwayat(){

let data=JSON.parse(localStorage.getItem("riwayatGuru"))||[];

let html="";

if(data.length==0){

html="<div class='alert alert-secondary'>Belum ada riwayat.</div>";

}else{

data.forEach(function(item){

html+=`

<div class="item">

<b>${item.tanggal}</b>

<br>

Guru Hadir : ${item.guru}

<br>

Ompreng : ${item.ompreng}

<br>

Jatah / Orang : ${item.jatah}

</div>

`;

});

}

document.getElementById("isiRiwayat").innerHTML=html;

}
</script>

</body>

</html
