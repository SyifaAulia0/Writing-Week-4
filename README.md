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
