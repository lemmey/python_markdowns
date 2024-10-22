___
[[Python/datatypes/immutables/String]]
#ZEN
___
`Formatted Strings` fördern die Lesbarkeit bei langen Strings und erlauben erweiterte Formatierungsmethoden. So lassen sich z.B. numerische Werte/Variablen dynamisch als und in einen String integrieren.

```python
gefährten = 9

print(f'Die {gefährten} Gefährten sollen es mit den 9 Ringgeistern aufnehmen.')

# A different notation:

print('''Die {} Gefährten sollen es mit den {wraiths} Ringgeistern aufnehmen.'''.format(gefährten, wraiths=9))
```

### Numerische Mini-Formation

```python
x = 10
print(f'''{x}
{x=}
{x:.2f}\n''')

# 10
# x=10
# 10.00

y = 2139021487965
print(f'''{y:_}\n''')

# 2_139_021_487_965

z = 0.1
print(f'''{z:.0%}''')

# 10%
```

Es lassen sich auch if-Statements in f-Strings unterbringen, cool:

#condition
```python
condition = True

print(f'{"This condition is True" if condition else "This condition is False"}')

# This condition is True
```