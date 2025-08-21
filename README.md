# Marathi Verb Tense Conjugator (Demo)

This repository contains a simple Python function that generates verb forms for **different tenses** by attaching suffixes to a given verb root.  
It is a **demo model** to illustrate basic tense patterns in Marathi, not a complete or linguistically accurate conjugator.

---

## 🔹 How It Works
The function `marathi_verb_tense(verb, tense)` takes:
- **verb**: a verb root in Latin script (for simplicity, e.g., `"kha"`, `"bol"`, `"zop"`)  
- **tense**: one of `"present"`, `"past"`, `"future"`, `"imperative"`  

It then looks up suffixes for **person + number** (first, second, third; singular, plural) in a dictionary.  
For imperatives, only **second person singular/plural** are supported.  

---

## 🔹 Rule Mapping

### Present
- First Singular → `to`
- Second Singular → `tos`
- Third Singular → `to`
- First Plural → `to`
- Second Plural → `ta`
- Third Plural → `tat`

### Past
- First Singular → `lo`
- Second Singular → `las`
- Third Singular → `la`
- First Plural → `lo`
- Second Plural → `lat`
- Third Plural → `le`

### Future
- First Singular → `n`
- Second Singular → `shil`
- Third Singular → `l`
- First Plural → `lu`
- Second Plural → `ɻal`
- Third Plural → `til`

### Imperative
- Second Singular → `e`
- Second Plural → `o`

---

## 🔹 Code

```python
def marathi_verb_tense(verb, tense):
    # Define the verb conjugation rules for different tenses
    verb_conjugation = {
        'present': {
            'first_singular': verb + 'to',
            'second_singular': verb + 'tos',
            'third_singular': verb + 'to',
            'first_plural': verb + 'to',
            'second_plural': verb + 'ta',
            'third_plural': verb + 'tat'
        },
        'past': {
            'first_singular': verb + 'lo',
            'second_singular': verb + 'las',
            'third_singular': verb + 'la',
            'first_plural': verb + 'lo',
            'second_plural': verb + 'lat',
            'third_plural': verb + 'le'
        },
        'future': {
            'first_singular': verb + 'n',
            'second_singular': verb + 'shil',
            'third_singular': verb + 'l',
            'first_plural': verb + 'lu',
            'second_plural': verb + 'ɻal',
            'third_plural': verb + 'til'
        },
        'imperative': {
            'second_singular': verb + 'e',
            'second_plural': verb + 'o'
        }
    }

    # Get the verb form based on the tense
    if tense in verb_conjugation:
        verb_form = verb_conjugation[tense]
    elif tense == 'third_singular':
        verb_form = verb_conjugation['past']['third_singular']
    elif tense == 'first_plural':
        verb_form = verb_conjugation['present']['first_plural']
    elif tense == 'second_plural':
        verb_form = verb_conjugation['present']['second_plural']
    elif tense == 'third_plural':
        verb_form = verb_conjugation['present']['third_plural']
    else:
        verb_form = verb_conjugation['past']['third_plural']

    return verb_form
``` 

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
```
---

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

