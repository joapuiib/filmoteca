<HighLevelDetails>

The `filmoteca` repository stores cultural data collections in three main folders:
- `llibres/` → book entries
- `pelicules/` → movie entries
- `series/` → series entries

Each folder contains a `README.md` that describes the exact format each entry must follow.  
Each entry is a text file (usually `.md` or `.txt`) with fields such as title, author/director, year, etc.  
The repository **does not contain any scripts or executable code** — only data files.

Goal:
- Enable Copilot to **verify that each entry file complies with the format specified in its README**.
- Ensure that **no entries are duplicated** (same title, author, or file name).

Project type: data collection.  
Languages: Markdown / plain text.  
No dependencies or compilation.  
Repository is small and can be fully analyzed.

</HighLevelDetails>

<BuildInstructions>

There is no build or execution process.  
Copilot should analyze the files directly.

Do not execute any commands or create any scripts.  
All verification should be done internally by Copilot's analysis.

</BuildInstructions>

<ProjectLayout>

Typical project structure:

```
filmoteca/
├── llibres/
│   ├── README.md          → specifies expected format for each book
│   ├── llibre1.md
│   ├── llibre2.md
│   └── ...
├── pelicules/
│   ├── README.md          → specifies expected format for each movie
│   ├── peli1.md
│   └── ...
├── series/
│   ├── README.md          → specifies expected format for each series
│   ├── serie1.md
│   └── ...
└── README.md              → general description of the project
```

No source code or configuration files exist.  
Validation relies solely on matching files to the formats documented in the `README.md`.

</ProjectLayout>

<LanguageMapping>

Entries may be written in Catalan, Spanish, or English. The language of an entry can differ from the language of the README, but **all headings and field names within a single file must use the same language**.

Use the following allowlist when validating headings and field names. Treat each row as a set of equivalent terms — any one of them is acceptable for that concept:

### `llibres/` — Section headings

| Concept       | Catalan           | Spanish            | English       |
|---------------|-------------------|--------------------|---------------|
| Synopsis      | `## Sinopsi`      | `## Sinopsis`      | `## Synopsis` |
| Genres        | `## Gèneres`      | `## Géneros`       | `## Genres`   |

### `llibres/` — Field names

| Concept          | Catalan                 | Spanish                  | English       |
|------------------|-------------------------|--------------------------|---------------|
| Author           | `__Autor__`             | `__Autor__`              | `__Author__`  |
| Publication year | `__Any de publicació__` | `__Año de publicación__` | `__Year__`    |

### `pelicules/` — Section headings

| Concept       | Catalan             | Spanish            | English       |
|---------------|---------------------|--------------------|---------------|
| Synopsis      | `## Sinopsi`        | `## Sinopsis`      | `## Synopsis` |
| Genres        | `## Gèneres`        | `## Géneros`       | `## Genres`   |
| Cast          | `## Repartiment`    | `## Reparto`       | `## Cast`     |

### `series/` — Section headings

| Concept       | Catalan             | Spanish            | English       |
|---------------|---------------------|--------------------|---------------|
| Synopsis      | `## Sinopsi`        | `## Sinopsis`      | `## Synopsis` |
| Genres        | `## Gèneres`        | `## Géneros`       | `## Genres`   |
| Seasons       | `## Temporades`     | `## Temporadas`    | `## Seasons`  |
| Cast (opt.)   | `## Repartiment`    | `## Reparto`       | `## Cast`     |

_Note_: Treat **Seasons/Temporades** as a core section for series if the `series/README.md` specifies it. The **Cast** section is optional and should only be required if explicitly indicated by the `series/README.md`.
</LanguageMapping>

<StepsToFollow>

1. Examine all contents of the `filmoteca` repository.
2. Read all `README.md` files to understand the **required sections and fields** for each type of entry (treat the README as defining the structure conceptually, not as providing the exact heading strings to match).
3. List all files in `llibres/`, `pelicules/`, and `series/` (ignoring `README.md`).
4. For each file:
   - Verify that all required sections and fields are present, using the language mapping in `<LanguageMapping>` to accept any valid language variant for each concept.
   - Identify missing, incorrect, or misordered sections/fields.
   - Check that the language is consistent within the file: all headings and field names must use the same language (Catalan, Spanish, or English).
   - The language of the file may differ from the language of the README.
5. Detect potential duplicates based on:
   - title,
   - file name,
   - or other key fields defined in the README.
6. Produce a report listing:
   - Correct entries ✅
   - Entries with format issues ⚠️ (indicating missing fields)
   - Duplicate entries ❌ (indicating affected files)
7. Do not generate or execute any code or modify any files.
8. Use internal analysis of the repository. Only perform additional searches if the instructions are incomplete or contradictory.
9. Treat the `README.md` files as the authoritative source for **which sections and fields are required**; use the `<LanguageMapping>` table to determine valid heading/field names for each supported language.

</StepsToFollow>
