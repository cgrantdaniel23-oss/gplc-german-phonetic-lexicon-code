# gplc-german-phonetic-lexicon-code
A multi-letter uppercase ASCII phonetic transcription standard for German. An alternative to SAMPA optimized for clean string parsing in modern TTS/ASR pipelines.


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
| **A** | Short Vowel | M**a**nn | Crisp, short "ah" |
| **AP** | Long Vowel (A Prime) | B**ah**n | Stretched, open "aaah" |
| **E** | Short Vowel | B**e**tt | Short "eh" as in *bet* |
| **EP** | Long Vowel (E Prime) | S**ee** | Long trailing "ay" sound |
| **I** | Short Vowel | m**i**t | Short "ih" as in *bit* |
| **IP** | Long Vowel (I Prime) | m**i**r / w**ie** | Stretched "ee" sound |
| **O** | Short Vowel | K**o**pf | Short "oh" sound |
| **OL** | Long Vowel (O Prime) | B**oo**t | Deep, long "oh" sound |
| **U** | Short Vowel | H**u**nd | Short "uh" as in *put* |
| **UL** | Long Vowel (U Prime) | Sch**uh** | Long, deep "oooh" sound |

### 2. Umlauts & Blends

| GPLC Token | Sound Property | Native German Example | Pronunciation Guide |
| :--- | :--- | :--- | :--- |
| **AE** | Short Umlaut | H**ä**nde | Short open "eh" |
| **AEP** | Long Umlaut (Ä Prime) | K**ä**se | Long drawn-out "ehhh" |
| **OE** | Short Umlaut | k**ö**nnen | Short rounded "ö" |
| **OEP** | Long Umlaut (Ö Prime) | sch**ö**n | Long smooth "ööö" |
| **UE** | Short Umlaut | f**ü**nf | Short sharp "ü" |
| **UEP** | Long Umlaut (Ü Prime) | T**ü**r | Long continuous "üüü" |
| **AY** | Diphthong Blend | m**ei**n | Sounds like the English word *my* |
| **AW** | Diphthong Blend | H**au**s | Sounds like the English word *house* |
| **OY** | Diphthong Blend | n**eu** | Sounds like the English word *boy* |
| **AXR** | Unstressed End Vowel | bitt**e** | The soft "uh" schwa sound |
| **RX** | Vocalic End R | Vat**e**r | The vocalized, soft "er" drop |

### 3. Core & Unique German Consonants

| GPLC Token | Sound Property | Native German Example | Pronunciation Guide |
| :--- | :--- | :--- | :--- |
| **KH** | Velar Fricative (Ach-Laut) | a**ch** / Do**ch** | Rough throat sound after A, O, U |
| **CH** | Palatal Fricative (Ich-Laut) | i**ch** / Re**ch**t | Soft, hissing sound after E, I, Ä, Ö, Ü |
| **SH** | Sibilant Fricative | **Sch**uh | Standard English "sh" sound |
| **ZH** | Voiced Sibilant | **G**enie | Smooth "zh" as in *measure* |
| **TS** | Sharp Affricate | **Z**eit | Crisp "ts" combination |
| **PF** | Explosive Affricate | **Pf**erd | Pop "p" instantly rolling into "f" |
| **GL** | Glottal Stop | ver**-**ein | Quick catch of breath between vowels |
| **NG** | Velar Nasal | ju**ng** | Smooth nasal "ng" |
| **B** | Plosive | **b**lau | Standard "b" sound |
| **P** | Plosive | **p**lanen | Standard "p" sound |
| **D** | Plosive | **d**ann | Standard "d" sound |
| **T** | Plosive | **t**un | Standard "t" sound |
| **G** | Plosive | **g**ut | Standard "g" sound |
| **K** | Plosive | **k**alt | Standard "k" sound |
| **M** | Nasal | **m**ein | Standard "m" sound |
| **N** | Nasal | **n**ein | Standard "n" sound |
| **F** | Fricative | **f**rei | Standard "f" sound |
| **V** | Fricative | **w**enn | Standard voiced English "v" sound |
| **S** | Fricative | da**s** | Standard hiss "s" sound |
| **Z** | Fricative | **s**agen | Standard buzzed voiced "z" sound |
| **H** | Fricative | **h**ier | Standard breathy "h" sound |
| **R** | Liquid Consonant | **r**ot | Standard German friction/trilled "r" |
| **L** | Liquid Consonant | **l**ang | Standard "l" sound |
| **Y** | Semivowel | **j**a | Standard English "y" sound as in *yes* |

---

## Transcription Mapping Example

Text sentences pass through an execution loop, spitting out clean pipelines separated by standard tracking pipes (`|`):

* **Written German**: `Ich bin ein Vater bitte schön.`
* **GPLC Pipeline Stream**: `I CH | B I N | AY N | F AP T RX | B I T AXR | SH OEP N`

---

## License

This formatting standard is released under the MIT License. Feel free to use, adapt, and build downstream computational linguistics utilities using the GPLC layout.
