# Marathi Verb Pluralisation

This repository contains a simple Python function that generates verb forms by attaching suffixes to a given verb root based on gender and number.  
It is a **demo model** to demonstrate basic morphological rules in Marathi, not a linguistically complete conjugator.

---

## 🔹 How It Works
The function `marathi_verb_pluralisation(verb, gender, number)` takes:
- `verb`: a verb root in Latin script (technically you can take Marathi Script for this, but for my convenience I have used Latin Script as we commonly use Hinglish/Minglish on Whatsapp and I wanted to try with this first) (e.g., `"kha"`, `"ja"`, `"bol"`)  
- `gender`: `"masculine"`, `"feminine"`, or `"neuter"`  
- `number`: `"singular"` or `"plural"`

It then looks up the suffix from a predefined dictionary and concatenates it to the root.  

### Rule Mapping
- Masculine + Singular → `āt`  
- Masculine + Plural → `at`  
- Feminine + Singular → `ti`  
- Feminine + Plural → `ti`  
- Neuter + Singular → `t`  
- Neuter + Plural → `at`  

---

## 🔹 Code

```python
def marathi_verb_pluralisation(verb, gender, number):
    # Define the verb conjugation rules
    verb_conjugation = {
        ('masculine', 'singular'): verb + 'āt',
        ('masculine', 'plural'): verb + 'at',
        ('feminine', 'singular'): verb + 'ti',
        ('feminine', 'plural'): verb + 'ti',
        ('neuter', 'singular'): verb + 't',
        ('neuter', 'plural'): verb + 'at'
    }

    # Get the verb form based on the subject's gender and number
    verb_form = verb_conjugation[(gender, number)]

    return verb_form

## What I coded

print(marathi_verb_pluralisation('kha', 'masculine', 'singular'))   # khaāt
print(marathi_verb_pluralisation('ja', 'masculine', 'plural'))      # jaat
print(marathi_verb_pluralisation('bol', 'feminine', 'singular'))    # bolti
print(marathi_verb_pluralisation('chal', 'feminine', 'plural'))     # chalti
print(marathi_verb_pluralisation('mar', 'neuter', 'singular'))      # mart
print(marathi_verb_pluralisation('radd', 'neuter', 'plural'))       # raddat
print(marathi_verb_pluralisation('zop', 'feminine', 'singular'))    # zopti
print(marathi_verb_pluralisation('bhet', 'feminine', 'plural'))     # bhetti
print(marathi_verb_pluralisation('pi', 'neuter', 'singular'))       # pit
print(marathi_verb_pluralisation('bagh', 'neuter', 'plural'))       # baghat
print(marathi_verb_pluralisation('sang', 'feminine', 'singular'))   # sangti

---

### Output

khaāt
jaat
bolti
chalti
mart
raddat
zopti
bhetti
pit
baghat
sangti

---

##🔹 Input Requirements

gender must be one of: masculine, feminine, neuter

number must be one of: singular, plural

verb must be a verb root in plain Latin script without spaces

---

##🔹 Limitations

This script is not linguistically accurate and does not cover real tense/aspect conjugations.

It does not handle exceptions, irregular verbs, or the actual Devanagari script.

It is for demonstration and educational purposes only.

---

##🔹 Future Improvements

Add input validation and error handling

Extend rules to cover tenses and aspects

Add support for Devanagari script output (e.g., खा → खातो, खातात)

Package the function with tests and CI/CD for Python
