############################

############################
# ALGORITHM SORT
############################

############################

# Sıralama Algoritmaları (or Sorting Algorithms)

## natural ordering
It is human readable.

traditional sort:

```
img1.png
img10.png
img12.png
img2.png
```

__natural sort__:

```
img1.png
img2.png
img10.png
img12.png
```

There is no any standard about how natural sorting should work exactly. Especially for special characters, lower and upper cases all implementations sorts the elements in different order. Natural sorting is designed to sort alphanumeric strings.

There are multiple algorithms to natural sort a string array. In some resources, the non-alphanumeric characters are ignoring directly. And each string is dividing in different parts, so it will be easier to sort it:

```
foo       =>  "foo",  -1
foobar    =>  "foo",  -1,  "bar"
foo13     =>  "foo",  13,
foo13xyz  =>  "foo",  13,  "xyz"
```

"GNU ls" command has "version sort" feature. If that feature will be enabled (by sending a parameter to cammand) it sorts the result based on natural sorting.

## lexicographic (or lexicographical order or lexical order or dictionary order)
- It is a general term of sorting string arrays.
- It has multiple variants:
  - alphabetical order
  - alphanumerical order

# Features of the sorting algorithms

- __Stability__

  If it is not necessary the elements does not shift.

  Let assume that we sort a table by it's "Name" column (the table example is below). If we don't shift the rows which have the same names, it would be performance advantage for us.

  ```
  Name   ID
  Ahmet  101
  Ahmet  102
  Ahmet  103
  Mehmet 105
  ```

- __in-place algorithm__

  The algorithms which does not require extra space (memory). Algortihms would require some small variables like:
  - counter
  - current index
  - max value of current array
  
  But those values are ignored.

  If an algorithm requires extra memory space to store a part of original array, they called __not-in-place (or out-of-place)__.

# Sorting Algorithm (or Sıralama algoritmaları)

- ## Kabarcık Sıralaması (or Baloncuk sıralaması or Bubble Sort)

Diziyi eleman sayısı kadar dolaşır. Her dolaşmada her elemanı sağ taraftaki ile kontrol edip yer değiştirtir.

- ## Seçerek Sıralama (or Selection Sort)

Diziyi sürekli dolaşır. En ufak elemanı geçici bir dizinin başına atar. Daha sonraki dolaşımlarda tekrar en ufak elemanı bulur geçici dizideki 2inci elemana atar.

- ## Hızlı Sıralama Algoritması (or Quick Sort Algorithm)

bir eleman seçilir. bu eleman pivot (Türkçe ve İngilizce'de bu şekilde kullanılır) adı verilir. bu elemanın, hangi index'teki eleman seçileceği hakkında birçok farklı görüş mevcuttur.

her pivotun sağ tarafında ondan büyük elemanlar yerleştirilir ve sol tarafında ise küçük elemanlar yerleştirilir. aynı işlem, sağ ve sol taraf içinde yapılacaktır. böyle olunca en ufak parçalara (3 elemana düşünceye kadar) bölündüğünde tekrar birleştirdiklerinde dizi sıralanmış olacaktır.

pivotun sağ ve sol tarafına yerleştirme işlemi şu şekilde yapılır: dizinin ilk ve son elemanı pivot ile karşılaştırılır. eğer ilk-elemen>=pivot>=son-eleman ise ilk-eleman ve son-eleman swap (yer değiştirir) edilir. Daha sonra dizinin baştan ikinci ve sonradan ikinci elemanı için aynı işlem yapılır. sonra 3üncü... tabi dizinin ortasına gelene kadar.

Buradan sonra dizinin sağ ve sol tarafı ayrı ayrı rekürsif olarak quick-sort algoritmasına sokulur. Burada ayrı ayrı quick-sort'a atılan dizilerin referanslarını quick-sort metotuna geçmemiz yeterli. yeni bir liste oluşturup klonlamaya gerek yok.

- ## Birleştirme Sıralaması (or Merge Sort)

Diziyi sürekli ikiye böler. her elemanı kendi içinde 2 şerli şekilde sıralar. Sonra bunları birleştirir. Birleştirirken de elemanların büyüklüklerini değerlendirir.

- ## Yığınlama Sıralaması (or Heap Sort)

öncelikle sıralanması istenen dizi heap ağacı kurallarına uygun şekilde ağaç haline getirilir. heap ağacı hale getirilmesi kısadır. büyük olan üstte ufak olan altında şeklinde dallandırılacaktır. fakat ağaç bir dizi yapısı olmadığından henüz elimizde sıralı bir dizi yoktur. bunu dizi hale getirmek gerekmektedir. heap ağacının en üstündeki en üst sayı olacağından, sonuç kümesine en büyük rakam olarak kaydedilir. daha sonra ağacın en üstteki node'u silerek ağaç tekrar heapfy işlemine sokulur. bu sefer ağacın en üstündeki değer sonuç kümemizin ikinci en büyük sayısı olmuş olur. bu şekilde tüm ağaç sıfırlandığında sonuç kümemizde sıralanmış bir dizi olacaktır.
