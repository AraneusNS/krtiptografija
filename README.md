# krtiptografija
Softversko inženjerstvo, zimski semestar, godina II

Data Encryption Standard (DES) Permutacije
Koriste se:
  1. Permutacija
  2. Supstitucija (Skutije)

Rad u rundama (broj rundi > 2n+2, n>0).

Dva ulaza:
64 bitni blok teksta (poruke).
56 bitni ključ (svaki osmi je bit parnosti)

Kao osnovu DES-a koristi se Feistel-ova mreza


DES predstavlja kriptovanje koje transofmiše 64 bitne blokove podataka u 64 bitne kriptovane blokove podataka. Dužina ključa kriptovanja je 64 bita, od kojih 8 otpada na proveru pariteta, tako da je efektivna dužina ključa 56 bita.
DES kriptovanje i dekriptovanje se sprovodi u nekoliko koraka. Prvo se bitovi ulaznog bloka dužine 64 bita permutuju nekom inicijalizovanom permutacijom - IP. Tada se ulazni blok podeli na dva dela po 32 bita, levi L0 i desni deo R0. Nad desnim blokom se obavlja funkcija F(Ri, Ki), odnosno F(Ri,K(16-i+1)) kod dekriptovanja, gde je Ri desnih 32 bita, a Ki je 48 bitni ključ koji se generiše iz zadanog tajnog ključa kriptovanja. Vrednost dobijena operacijom XOR između vrednosti funkcije F i levih 32 bita podataka, postaje R(i+1), tj. desnih 32 bita za sledeći korak iteracije. L(i+1) za sledeći korak je Ri. Nakon 16 takvih koraka blokovi se zamenjuju te se spajaju i obavlja se konačna permutacija koja je inverzna početnoj permutaciji, tj. IP^(-1). Dobijenih 64 bita su kriptovani blokovi. Budući da se nakon dve uzastopne operacije XOR sa istim brojem dobija početna vrednost, tj. a = (aĹ b)Ĺ b, postupak dekriptovanja može se sprovesti tako da se operacije obavljaju obrnutim redosedom. Zbog simetričnosti algoritma to se postiže tako da se kriptovani blok pusti kroz isti algoritam sa tom razlikom da se umesto ključa Ki u i-tom koraku upotrebi ključ K(16-i+1).
Postupak generisanja šestnaest 48 bitnih ključeva od zadanog, tajnog ključa sprovodi se u nekoliko koraka. Prvo se pomoću zadane tablice permutacije iz ključa generišu dva bloka po 28 bita. Zatim sledi 16 sledećih koraka: svaki se blok rotira u levo za određeni broj bita (u zavisnosti o kojem je koraku reč) te se iz nastalih blokova (2 × 28) pomoću tablicom zadate permutacije generiše ključ Ki, gde je i broj koraka. Funkcija enkripcije F jeste zapravo najkritičniji deo algoritma, tj. upravo zbog njene kompleksnosti ne postoji (barem koliko je za sada poznato) način provaljivanja DES-a (osim grubom računarskom silom). Vrednost funkcije dobija se u nekoliko koraka. Najpre se od ulaznih 32 bita Ri proširenjem zadanom tablicom dobija 48 bita. Ta se vrednost sabira logičkom operacijom XOR sa ključem Ki paralelno nad svakim bitom. Dobijena se 48 bitna vrednost deli na osam delova od po šest bita. Prvi i zadnji bit svakog dela predstavlja adresu reda, a srednja četiri adresu kolone u tablici selekcije, odnosno, pomoću šest određena su četiri bita. Istim postupkom nad svakom šestorkom od ulaznih 48 bita selekcijom dobijamo 32 bita. Tih se 32 bita još permutuje zadatom tablicom te se dobija konačna vrednost funkcije F.
