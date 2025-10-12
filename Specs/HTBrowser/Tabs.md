# Tabs

Tab is a URL file. A URL file consists of information in a tab. It uses a common format of **`JSON`**. It collects importantly the `URL` which is website you'd like to go. Additionally:

- `title` = Modifiable Tab title. If empty, then it uses default tab title from its html `head`.
- `engine` = Sets default browser when one would like to open this tab JSON file.
- `extraUrls` = Array for Tab splits.
- the `rem` (remarks) is unused and used to pad JSON's limitation of no trailing coma rules.

```json
{
    "title": "Modified name",
    "url": "https://example.com",
    "extraUrls":
    [
        {
            "title": "split 1",
            "url": "https://split1.example.com",
        },
        {
            "title": "split 2",
            "url": "https://split2.example.com",
        }
    ],
    "engine": "ladybird",
    "rem": "hello world"
}
```

## Categorizing

Tab files can be wildly put in which folders you'd like to categorize your tab. Tab Managers should work like a File Manager or Programming IDE, where its file list left sidebar lists all the tabs, maybe foldered, and can be sorted at anytime. It is very important to make sure tab managing performance & mechanism is exactly the same or better as managing files in general.

```
📂 Not yet Downloaded:
    📦 Example File | Repo Model
    📦 Example File2 | Repo Model
    📦 Example File3 | Repo Model
    📦 Bethoven Pack for Leekspinner Vol. 5 MIDI 2.0 & MPE | MIDI Havens
    📂 Supremo:
        📦 Supremo Vol. 1 | Repo Model
        📦 Supremo Vol. 2 | Repo Model
    📦 Retro Computer 86Box Prepacks | Wild Files

📂 OK:
    📦 Dice Card Self Assembly STL | Repo Model
    📦 Benchy STL | Repo Model
```

e.g., if you already downloaded `Example File | Repo Model`, you will move that Tab JSON file to `OK` folder.