# Writing-Week-4
## Async await, Promises, Fetch
- Prosesnya :
  - front-end -> API -> (server -> database) backend 
- API adalah jembatan komunikasi ke server untuk mendapatkan data
- data yang dikirim dan diterima oleh API dalam bentuk JSON (JavaScript Object Notation)
- ciri-ciri json : setiap property ada tanda kutipnya

### promises
- API menggunakan promises
- kodingan promises  menggunakan : .namaPromises .then() .catch() 
- contoh
```js
//object promises
let nonton = (kondisi) => {
    return new Promise((resolve, reject) => {
      if (kondisi == "jalan") {
        resolve("nonton terpenuhi")
      }
      reject("batal nonton")
    })
  }
```
- untuk memanggil dan menjalankan object promises di atas, ada 2 cara :
1. menggunakan .then() .catch()
2. menggunakan async await
```js
//promises .then() .catch()
nonton("jalan") .then(result => {
    console.log(result); //nonton terpenuhi
  }).catch(err => {
    console.log(err)
  })
```
### async await
```js
//async await
//buat async function
async function asyncNonton() {
    try {
      let result = await nonton("jalan")
      console.log(result); //nonton terpenuhi
    } 
  asyncNonton()
```
```js
async function asyncNonton() {
    try {
      let result = await nonton()
      console.log(result);
    } catch (error) {
      console.log(error)  //batal nonton
    }
  }
  asyncNonton()
```
### fetch
- fetch merupakan object promises 
- fetch di handle menggunakan promises dan async await
```js
//data digimon didapatkan dari data digimon di google
//result.json digunakan untuk membuka/unboxing isi dari data digimon
//jika tidak menggunakan result.json data akan pending
fetch("https://digimon-api.vercel.app/api/digimon") 
  .then(result => result.json())
  .then(result => {
    console.log(result)
  })
```
## git dan github lanjutan
### berkolaborasi menggunakan github
- misal : A (team leader) membuat login, dan B (anggota) membuat register
- Langkah-langkah di github :
  1. buat repository organization, lalu invite anggota tim di fitur people, kemudian jadikan owner
    - jika menggunakan repository masing2, maka repository harus diberi akses ke anggota tim lain, kemudian invite tim anggotanya
  2. lalu buat repository, repo dibut public
  3. lalu buat branch bernama dev
- langkah selanjutnya pada git :
  1. buka git
  2. kemudian ketik git clone di git git clone untuk donlot repository ke file
  3. anggota membuat branch dari dev (*semua anggota ahrus konsisten membuat nama branch*)
  4. setiap anggota membuat branch masing2 
    - orang A : git switch dev, git branch A-login, git switch A-login (*checkout dan switch fungsinya sama*)
    - orang B : git switch dev, git branch B-register, git switch B-register 
    (*jika hanya ada satu branch, maka semua file akan masuk langsung ke main dan akan ada banyak bug*)
  5. buat file html , kemudian commit seperti biasa
  6. jika sudah commit, maka push -> git push –u origin (namabranch)
  7. lalu mengajukan pull request
    - *jika tim leader* maka klik pull request, lalu merge pull request
    - *jika anggota* klik request, lalu klik assign ke tim leader
    -	Pull request : mengajukan permintaan branch punya kita ke branch lain
  8. Jika tim leader sudah menerima request dari anggota, maka harus di cek dahulu dan kerjaannya sudah oke, maka beri label *buat label optional*
  9. Lalu klik merge pull request
  10. Lalu kembali ke git, dan kembali ke dev -> git switch dev
  11. Kemudian masukan kodingan -> git pull


