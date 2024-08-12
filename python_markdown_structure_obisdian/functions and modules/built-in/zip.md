___
[[functions]]
#built-in 
___
Die Funktion gibt ein erstmal ein zip-Objekt zurück, i.d.R. eine Liste aus Tuples. Bei unterschiedlicher Länge bestimmt der kürzeste Tuple die allgemeine Größe.

```python
wizards = ['Gandalf', 'Radagast', 'Sauron']
color = ['grey', 'brown', 'black']
ethos = ['good', 'neutral', 'evil']

zip_wizards  = list(zip(wizards, color, ethos))

# [('Gandalf', 'grey', 'good'), ('Radagast', 'brown', 'neutral'), ('Sauron', 'black', 'evil')]
```

Tipp: Es kann auch ein strict Boolean gestellt werden, damit gibt zip( ) einen Exception-Error falls die Objekte unterschiedlich lang sind. So kann z.B. verhindert werden, dass Daten übersprungen werden.