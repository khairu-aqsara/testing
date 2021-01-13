### 1
Buat sebuah fungsi PHP untuk mencari tau apakah sebuah nilai merupakan nilai yang dihasilkan oleh perkalian dari `2 angka prima`, misalnya `fungsi(25) = true` karena `25` merupakan hasil perkalian dari `5 x 5` dimana `5` merupakan angka prima.

```php
<?php
function Periksa($num){
    $p=2;
    $c=1; 
    while($num >= $p*$p){
        if( $num % $p < 1 ){
            $c+=1;
            $num/=$p;
        }else{
            $p+=1;
        }
    }
    return $c==2;
```

### 2
buat fungsi PHP untuk menghitung Jumlah Huruf dan Angka dari sebuah string, kembalian dari fungsi harus berbentuk array, misalnya `hitung('Nama Saya') = ['HURUF'=>8, 'ANGKA'=>0]` atau `hitung('Umur 20') = ['HURUF'=>4, 'ANGKA'=>2]`

```php
<?php
#cara 1
function Hitung($str) {
    preg_match_all('/([a-zA-Z])|(\d)/', $str, $matches);
    return [
        'HURUF' => strlen(implode($matches[1])),
        'ANGKA' => strlen(implode($matches[2]))
    ];
}

#cara 2
function HitungLagi($str) {
    return ["HURUF" =>  preg_match_all('/[a-z]/i', $str), "ANGKA" => preg_match_all('/\d/i', $str)];
}
```

### 3
Buat fungsi Javascript Lodash: _.groupBy javascript dengan versi kelian sendiri, contoh `Lodash: _.groupBy` versi javascript ada di https://www.geeksforgeeks.org/lodash-_-groupby-method/

```js
// Cara 1 Reusable Function
const group_by = (collection, q) => {
    collection = Object.values(collection);
    switch (typeof q) {
      case "string":
        return collection.reduce((a, c) => (a[c[q]] = [...(a[c[q]] || []), c], a), {});
      case "function":
        return collection.reduce((a, c) => (a[q(c)] = [...(a[q(c)] || []), c], a), {});
      default:
        const [[k, v]] = Object.entries(q);
        return collection.reduce((a, c) => (a[c[k] === v] = [...(a[c[k] === v] || []), c], a), {});
    }
};

let data = ['eight', 'nine', 'four', 'seven']
let data2 = [6.5, 4.12, 6.8, 5.4]
let grouped_data = group_by(data, 'length')
let grouped_data2 = group_by(data2, Math.floor)

// Cara Lainya
// Contoh singel Use
var contoh1 = [6.5, 4.12, 6.8, 5.4].reduce((r, v, i, a, k = Math.floor(v)) => ((r[k] || (r[k] = [])).push(v), r), {})
console.log(contoh1)

// Contoh singel Use
var contoh2 = ['eight', 'nine', 'four', 'seven'].reduce((r, v, i, a, k = v.length) => ((r[k] || (r[k] = [])).push(v), r), {})
console.log(contoh2)
```