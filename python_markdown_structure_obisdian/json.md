___
[[documentation]]
#json
___
Das *JavaScript Object Notation* Dateiformat kann Teil der Python Dokumentation sein, aber genauso ein Rückgabeformat von vielen APIs, Configuration Files und Sicherheitsprotokollen. 
Vorteilhaft an dem Interchange-Format JSON ist, dass das Format mit den meisten Programmiersprachen, IDEs sowie Betriebssystemen wie Android kompatibel ist. 
Die Nähe zu JavaScript Syntax macht JSON zu einem uniform lesbaren Browserformat, ideal um Dateien z.B. von Klienten auf einen Server zu übertragen.
___
JSON Syntax Verschiedenheiten zu Python:

| Python       | JSON                         |
| ------------ | ---------------------------- |
| String       | only in `""` not `''`        |
| Booleans     | only lowercase: `true false` |
| Null         | lowercase: `null`            |
| Lists        | Arrays `[1, 2, "3"]`         |
| Dictionaries | Objects as `Key:Value` pairs |
|              |                              |
___
### Using JSON with Python

```python
import json
```
JSON Files werden in JSON-Strings oder Objekten geschrieben, welche einem Python #dictionary  ähnlich sind.

Einen JSON-String in ein Python Format laden (`load string`). Ein JSON-String ist wie ein Dictionary formatiert mit kleinen Syntax-Besonderheiten für JSON Lesbarkeit:
```python
py_data = json.loads(a_json_string)
```

Ein Python Dictionary in ein JSON-String dumpen (`dump string`):
```python
json_data = json.dumps(py_data, indent=4, sort_keys=True)
```
___
Eine .json-Datei lesen:
```python
with open('data.json', 'r', encoding='utf-8') as file:
	data = json.load(file) # now Python object/file
```

Eine .json-Datei schreiben:
```python
with open('data_new.json', 'w') as file:
	json.dump(data, file)
```
___
### JSON als (uniform lesbare) Configuration Datei

```python
import json

values = """

{

    "rgbs":{

        "Color1":[179, 78, 23],
        "Color2":[251, 12, 12],
        "Color3":[48, 66, 133]

        },

    "fonts": [

        "Helvetica",
        "Roboto",
        "Default"

        ]

        }

        """
  

settings = json.loads(values)

print(settings) # <class 'dict'>
# {'rgbs': {'Color1': [179, 78, 23], 'Color2': [251, 12, 12], 'Color3': [48, 66, 133]}, 'fonts': ['Helvetica', 'Roboto', 'Default']}
```

Mit einer benachbarten `.json` Datei (mit Namen `settings.json` im selben Verzeichnis):
```json
{

    "settings":

    [

        {

            "BLACK" : "#000000",

            "WHITE" : "#EEEEEE"

        },

        {

            "RGBS" : {

                "Color1":[179, 78, 23],

                "Color2":[251, 12, 12],

                "Color3":[48, 66, 133]

            }

        },

        {

            "FONTS" : ["Helvetica", "Roboto", "Default"]

        }

    ]

}
```

```python
import json

  

with open('py_test\\settings.json', 'r') as f:

    data = json.load(f)

print(data)
# {'settings': [{'BLACK': '#000000', 'WHITE': '#EEEEEE'}, {'RGBS': {'Color1': [179, 78, 23], 'Color2': [251, 12, 12], 'Color3': [48, 66, 133]}}, {'FONTS': ['Helvetica', 'Roboto', 'Default']}]}

x = data['settings'][0]['BLACK']
# Because its a dictionary with a list of dictionaries ... not ideal
print(x) # #000000
```
