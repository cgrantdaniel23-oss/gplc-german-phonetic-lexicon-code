# GPLC: German Phonetic Lexicon Code (v1.0.0)

GPLC (German Phonetic Lexicon Code) is an open-source, machine-readable phonetic transcription standard for the German language. 

Unlike traditional symbol-dependent formats like SAMPA or the International Phonetic Alphabet (IPA), GPLC utilizes a strict system of **uppercase, multi-letter ASCII tokens**. This eliminates encoding bugs, makes data pipelines highly readable, and allows modern software engines to parse spoken pronunciations using simple space-separated string manipulation.

---

## Key Architecture & Philosophy

1. **Space-Separated Tokenization**: Every distinct phoneme is an independent string token. Computer scripts can instantly isolate individual speech units using standard split operations (`.split()`), which is highly optimized for modern Text-to-Speech (TTS) and Automatic Speech Recognition (ASR) systems.
2. **The Prime System**: To handle German's strict vowel lengths, GPLC appends a systematic suffix (`P` for Prime, or `L` for Long) to indicate long variations of short vowel baselines without changing case or adding raw punctuation marks.
3. **No Case Ambiguity**: Every code token is strictly UPPERCASE to prevent data line bugs common in character streams where `ch` and `CH` might accidentally collide.

---

## GPLC Specification Chart

### 1. Vowels & The Prime System

| GPLC Token | Sound Property | Native German Example | Pronunciation Guide |
| :--- | :--- | :--- | :--- |
| **A** | Short Vowel | M**a**nn | Vowel in English *bus* / short "ah" |
| **AP** | Long Vowel (A Prime) | B**ah**n | Stretched vowel in English *father* |
| **E** | Short Vowel | B**e**tt | Vowel in English *bet* |
| **EP** | Long Vowel (E Prime) | S**ee** | Vowel in English *say* (without the trailing "y" sound) |
| **I** | Short Vowel | m**i**t | Vowel in English *bit* |
| **IP** | Long Vowel (I Prime) | m**i**r / w**ie** | Vowel in English *meet* |
| **O** | Short Vowel | K**o**pf | Short open "o", like British English *not* |
| **OL** | Long Vowel (O Prime) | B**oo**t | Vowel in English *boat* (pure "oh" sound) |
| **U** | Short Vowel | H**u**nd | Vowel in English *put* |
| **UL** | Long Vowel (U Prime) | Sch**uh** | Vowel in English *boot* |

### 2. Umlauts & Blends

| GPLC Token | Sound Property | Native German Example | Pronunciation Guide |
| :--- | :--- | :--- | :--- |
| **AE** | Short Umlaut | H**ä**nde | Same as **E** (vowel in *bet*) |
| **AEP** | Long Umlaut (Ä Prime) | K**ä**se | Stretched "eh" sound, like vowel in English *care* |
| **OE** | Short Umlaut | k**ö**nnen | Say **E** with lips rounded like you are saying **O** |
| **OEP** | Long Umlaut (Ö Prime) | sch**ö**n | Say **EP** with lips rounded like you are saying **OL** |
| **UE** | Short Umlaut | f**ü**nf | Say **I** with lips rounded like you are saying **U** |
| **UEP** | Long Umlaut (Ü Prime) | T**ü**r | Say **IP** with lips rounded like you are saying **UL** |
| **AY** | Diphthong Blend | m**ei**n | Vowel in English *my* |
| **AW** | Diphthong Blend | H**au**s | Vowel in English *house* |
| **OY** | Diphthong Blend | n**eu** | Vowel in English *boy* |
| **AXR** | Unstressed End Vowel | bitt**e** | The "schwa" sound, like the 'a' in *about* |
| **RX** | Vocalic End R | Vat**e**r | Non-rolled ending 'er', sounds like British *father* |

### 3. Core & Unique German Consonants

| GPLC Token | Sound Property | Native German Example | Pronunciation Guide |
| :--- | :--- | :--- | :--- |
| **KH** | Velar Fricative (Ach-Laut) | a**ch** / Do**ch** | Throat clearing friction sound, like Scottish *loch* |
| **CH** | Palatal Fricative (Ich-Laut) | i**ch** / Re**ch**t | Hissing air sound, like the 'h' in English *huge* |
| **SH** | Sibilant Fricative | **Sch**uh | Consonant in English *shoe* |
| **ZH** | Voiced Sibilant | **G**enie | Consonant in English *measure* / *vision* |
| **TS** | Sharp Affricate | **Z**eit | Sounds like the ending of English *cats* |
| **PF** | Explosive Affricate | **Pf**erd | A 'p' and 'f' pronounced simultaneously |
| **GL** | Glottal Stop | ver**-**ein | Sound between the syllables of *uh-oh* |
| **NG** | Velar Nasal | ju**ng** | Ending nasal sound in English *sing* |
| **B** | Plosive | **b**lau | English *b* |
| **P** | Plosive | **p**lanen | English *p* |
| **D** | Plosive | **d**ann | English *d* |
| **T** | Plosive | **t**un | English *t* |
| **G** | Plosive | **g**ut | English *g* in *go* |
| **K** | Plosive | **k**alt | English *k* |
| **M** | Nasal | **m**ein | English *m* |
| **N** | Nasal | **n**ein | English *n* |
| **F** | Fricative | **f**rei | English *f* |
| **V** | Fricative | **w**enn | English *v* in *vine* |
| **S** | Fricative | da**s** | English hiss *s* in *sit* |
| **Z** | Fricative | **s**agen | English voiced *z* in *zebra* |
| **H** | Fricative | **h**ier | English *h* |
| **R** | Liquid Consonant | **r**ot | Friction or rolled 'r' in the back of the throat |
| **L** | Liquid Consonant | **l**ang | English *l* |
| **Y** | Semivowel | **j**a | English *y* in *yes* |

---

## Transcription Mapping Example

Text sentences pass through an execution loop, spitting out clean pipelines separated by standard tracking pipes (`|`):

* **Written German**: `Ich bin ein Vater bitte schön.`
* **GPLC Pipeline Stream**: `I CH | B I N | AY N | F AP T RX | B I T AXR | SH OEP N`

---

## License

This formatting standard is released under the MIT License. Feel free to use, adapt, and build downstream computational linguistics utilities using the GPLC layout.
