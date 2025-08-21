# Marathi Verb Pluralisation

This repository contains a simple Python function that generates verb forms by attaching suffixes to a given verb root based on gender and number.  
It is a **demo model** to demonstrate basic morphological rules in Marathi, not a linguistically complete conjugator.

---

## 🔹 How It Works
The function `marathi_verb_pluralisation(verb, gender, number)` takes:
- `verb`: a verb root in Latin script (e.g., `"kha"`, `"ja"`, `"bol"`)  
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
