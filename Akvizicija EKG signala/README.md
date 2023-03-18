# Akvizicija EKG signala

EKG je proces mejrenja akcionog potencijala srca.

Srce je organ koji ima funkciju omogućavanja cirkulacije krvi kroz čitav organizam.
Prosječno srce ima masu od ~500 g, u najdužem pravcu je dužine 15 cm i to je orijentisano na dolje prema grudnoj šupljini. Zidovi srca su mišići koji odvajaju četiri dijela srca i to dvije pretkomore i dvije komore.
Između kontrakcija, srce se odmara i to se naziva dijastola. U toku dijastole srce se ispunjava krvlju i poprima najveće dimenzije. Krv prvobitno ulazi u lijevi dio srca, prolazi kroz pluća, i ovo se naziva pulminarni dio krvotoka. Nakon toga krv ulazi u desni dio srca gdlje biva ispumpano u čitavo tijelo. Period srčane aktivnosti naziva se sistola. Sistola započinje kontrakcijom srčanog mišića oko pretkomore (tj. atrijuma). Kontrakcije se šire do komora (tj. ventrikule). Ventrikule se skupljaju, povećavajući pritisak koji počinje da prevazilazi pritisak u ostatku sistema, zalisci se otvaraju prema aorti i krv se potiskuje iz srca. Nakon što se komore djelimčno isprazne, mišići koji odvajaju komore se opuštaju i aortni zalistak se opušta i tako počinje period dijastole.

U električnom smislu, srce se ponaša kao dipol.

![image](https://user-images.githubusercontent.com/122922214/226140205-889d47fe-4fc6-4adc-9e37-2349d9e736e2.png)

Desna pretkomora ima snop nerava (sinusatrijalni čvor - SA čvor). Ovaj skup ćelija inicira srčanu kontrakciju i on definiše ritam rada srca, tj. puls. Impuls koji je nastao u SA čvoru se prenosi do atrio-ventrikularnoh čvora (AV čvor) što izaziva impulse u miokardiu kroz Hisov snop i Purkinjeov sistem. Depolarizacija i repolarizacija SA čvora i AV čvora ima poseban značaj u radu srca.
Proces depolarizacije i repolarizacije se može snimati na površini kože u vidu EKG signala. EKG signal je ponovljiv, složenoperiodični signal na kome se mogu identifikovati neke pojave, tj. talasi.
Jedan srčani ritam kroz EKG signal se sastoji od P talasa koji je rezultat depolarizacije SA čvora. Depolarizacija nastupa odmah nakon toga i naziva se TA talas. Depolarizacija AV čvora ima naziv QRS kompleks.

![image](https://user-images.githubusercontent.com/122922214/226142414-b784d477-9223-496f-81f5-ff9497c55938.png)

Postavljanjem elektroda na različita mjesta na površini kože moguće je dobiti precizno ponašanje srca, njegovu orijentacjum, tj. orijentaciju dipola i vremenska promjena električnog polja dipola. Vektor električnog polja srca je orijentisan u prostoru stoga je potrebno mjeriti EKG zapis u sve tri ravni kartezijevog koordinatnog sistema.

## Uređaj za akviziciju EKG signala

Uređaj za akviziciju EGK signala treba da ima sljedeće osnovne sklopove
- Sklop za zaštitu i izolaciju koja sprječava da stuja koja može da dođe sa pacijenta preko elektroda ne ošteti uređaj (npr. prilikom defibrilacije)
- Predpojačavač - ovaj stepen pojačava ulazni signal. Njegovo pojačanje mora biti ~2000, treba da ima veliku ulaznu impedansu za diferencijalni, ali i za zajednički signal i veliki faktor potiskivanje srednje vrijednosti signala (CMRR, veći od 100 dB).
- Pojačavač koji omogućava vizuelizaciju podataka

Od tehničkih zahtijeva za uređaj to su:
- Linearnost i distorzija, odstupanje od linearnosti mora biti manje od 5% za izlazni signal.
- Ulazna impedansa između priključaka ne smije da bude manje od 5 megaoma. Instrument ne smije da dozvoli da postoji struja veća od 1 mA u kolu pacijent.

![image](https://user-images.githubusercontent.com/122922214/226141406-ec1aedfd-54b8-42dd-bd4b-022697c62495.png)

## Električni model ljudskog tkiva

Epidermis (koža) je barijera koja štiti tijelo od spoljnih uticaja. Njegova funkcija je takođe da zadrži vodu u organizmu, zaštiti organizam od ultraljubičastog zračenja. Epidermis je mekan i elastičan sloj ćelija koje mogu da ublaže posljedice mehaničkih udaraca na tijelo.

![image](https://user-images.githubusercontent.com/122922214/226141646-9eeabc02-ad23-4f86-9522-166bad129bbc.png)

![image](https://user-images.githubusercontent.com/122922214/226142059-ccfc66c6-7a7a-46e3-b032-2c4625e636c4.png)


Epidermis se modeluje paralelnom vezom kondenzatora vrijednosti ~50 nF i otpornika čija vrijednost je veća od 10 kilooma. Postavljanje elektrode na površinu kože ne ostvaruje idealan kontakt i u tom koraku se takođe unosi otpornost koja je najćešće manja od 1 kiloom, ali i površina elektrode se ponaša kao kondenzator, međutim ova kapacitivnost ne utiče previše na mjerenja. Usljed kontaktnog potencijala, na elektrodama dolazi do pojave napona. 

(https://www.analog.com/en/technical-articles/biopotential-electrode-sensors-ecg-eeg-emg.html)

![image](https://user-images.githubusercontent.com/122922214/226142434-f8c0d72c-b0bc-4b9a-9ea9-ccf35e71f0de.png)

## LT spice simulacija

EKG izvor se modeluje pomoću PWL naponskog izvora koji pruža opciju učitavanja fajla sa odmjercima koji definišu napon u datom trenutku.
Na repozitojiumu se nalazi tekstualni fajl ecg_source kojim se definiše naponski izvor. PWL naponskom izvoru treba dati puanju do ecg?source tekstualnog fajla.

![image](https://user-images.githubusercontent.com/122922214/226142801-ac00bce1-e375-4f55-89aa-36382afcbb5b.png)

Pokretanjem simulacije može se vidjeti naponski signal koji je generisan. Trajanje simulacije se može staviti da bude 6 sekudni, a najveći vremenski korak da vude 0.005.

![image](https://user-images.githubusercontent.com/122922214/226142939-6f0da409-be43-4974-8836-503281247b0a.png)

Kada se to uradi, dobija se sljedeći naponski oblik:

![image](https://user-images.githubusercontent.com/122922214/226142946-436b2580-2bba-4e6c-a459-f2f5359e1da4.png) ![image](https://user-images.githubusercontent.com/122922214/226142948-2194a5eb-ac9e-47b5-97d4-0eecf7016ca2.png)

PWL generator prolazi kroz odmjerke definisane u tekstualno fajlu i kada prodje kroz sve, naponski nivo genersian bivaju sve nule. Da bi simulirali periodične otkucaje srca, potrebno je u okviru PWL generatora unijeti naredbu repeat forever i tada se dovbija:

![image](https://user-images.githubusercontent.com/122922214/226143029-3ece81e1-102e-41c6-99d4-61c2c11cdee8.png)
 ![image](https://user-images.githubusercontent.com/122922214/226143020-1ac5c087-3889-436a-ae81-53a8a1b521d8.png)

Sada je modelovan izvor električnog signala koje generiše srce. Taj signal je u opsegu svega 2 - 3 milivolta. Sada ćemo modelovati i smetnju koja dolazi iz napona mreže usljed kapacitivnog vezivanja tijela osobe sa žicama elektrodistribucije 220 V, 50 Hz. Ovaj napon po amplitudi iznosi ~2V, ali može značajno da osciluje po amplitudi. Ovo se modeluje kao sinusni generator frekvencije 50 Hz i za potrebe vježbe stavljena amplituda je 2V, međutim ova ampltuda u stvarnosti je promjenljiva.
Sada izvor električnog signal izgleda ovako:

![image](https://user-images.githubusercontent.com/122922214/226143244-30d629a1-0264-4584-8d3e-26c9643c90b8.png)
 ![image](https://user-images.githubusercontent.com/122922214/226143246-825fd803-3d4e-4e2a-814f-6b59cf7e8682.png)


Korisni signal je utopljen u smetnje, tj. signal sada ima "zajedničku komponentu". Stavljaju se dvije elektrode na površinu kože i sada šema izgleda kao na sljedećoj slici:

![image](https://user-images.githubusercontent.com/122922214/226143328-f676001a-708d-4faa-9f3e-1ab19b2c9218.png)

Potrebno je signal na elektrodama obraditi na odgovarajući način i iz njega izvći EKG signal.

Za vježbu će se koristiti operacioni pojačavač LM358.
