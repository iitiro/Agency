# Agency

**AI-assisted analysis and coding of scholarly sources on subjectivity, identity, agency, selfhood, reflexivity, and lived experience.**

Agency is a research workflow for structured analysis of scholarly literature with language models. It combines source-level annotation, thematic coding, evidence extraction, relevance assessment, and article-specific reanalysis while preserving a distinction between source evidence and model-generated interpretation.

## Repository contents

| Path | Description |
|---|---|
| `scripts/01 literature_review_source_analysis.ipynb` | Corpus-wide annotation and coding of standalone and composite scholarly sources. |
| `scripts/02 core_article_analyses.ipynb` | Focused reanalysis of sources cited in a scholarly article, including claim auditing and cross-source synthesis. |
| `01 literature_review_annotations.xlsx` | Structured output from the literature-review workflow. |
| `02 core_article_analysis_results.xlsx` | Structured output from the article-specific reanalysis. |

## Main analytical functions

- source discovery and processing of TXT corpora;
- separate handling of standalone texts and multi-file composite sources;
- fragment-level analysis of long texts followed by source-level synthesis;
- thematic and conceptual coding;
- relevance assessment and section mapping;
- extraction and verification of source passages and definitions;
- article-claim auditing against cited primary sources;
- cache-aware processing to avoid unnecessary repeated API calls;
- export of structured results to Excel workbooks.

## Requirements

- Python 3.10 or later;
- Jupyter Notebook or JupyterLab;
- an OpenAI API key;
- Python packages: `openai`, `pandas`, `openpyxl`, and `python-docx`.

Example installation:

```bash
python -m venv .venv
source .venv/bin/activate
pip install jupyter openai pandas openpyxl python-docx
```

## Repository-local directory layout

The notebooks use portable paths and do not contain machine-specific directories. Their default layout is:

```text
Agency/
├── data/
│   ├── literature_corpus/
│   ├── article/
│   │   ├── paper.docx
│   │   └── reviewer.txt
│   └── article_reanalysis/
│       ├── article_sources_manifest.xlsx
│       └── sources/
├── outputs/
├── .cache/
└── scripts/
```

The source corpus is not included in this repository. Users are responsible for ensuring that they have the right to process the texts they supply.

## Configuration

Set the API key before running a notebook:

```bash
export OPENAI_API_KEY="your-api-key"
```

Alternatively, `OPENAI_API_KEY_FILE` may point to a local text file containing the key. The key file should never be committed to the repository.

Shared path overrides:

| Variable | Purpose |
|---|---|
| `AGENCY_PROJECT_ROOT` | Repository or project root. |
| `AGENCY_DATA_DIR` | Root directory for input data. |
| `AGENCY_OUTPUT_DIR` | Root directory for generated outputs. |
| `AGENCY_CACHE_DIR` | Root directory for cached model responses. |

The first notebook also supports `LITERATURE_INPUT_DIR`, `LITERATURE_OUTPUT_DIR`, `LITERATURE_RESULT_XLSX`, and `LITERATURE_CACHE_DIR`. Its paid analysis is disabled by default and can be enabled with `RUN_ANALYSIS=true`.

The second notebook supports `ARTICLE_DATA_DIR`, `ARTICLE_SOURCES_DIR`, `ARTICLE_MANIFEST_XLSX`, `ARTICLE_DOCX`, `REVIEWER_TXT`, `ARTICLE_OUTPUT_XLSX`, and `ARTICLE_CACHE_DIR`.

## Running the workflows

1. Place the source materials and supporting files in the default directories or define the corresponding environment variables.
2. Set `OPENAI_API_KEY`.
3. Open the required notebook in Jupyter.
4. Review its configuration cell, selected models, output language, and processing flags.
5. Run the cells in order.
6. Inspect the generated workbook and manually verify analytical conclusions and source quotations.

Model outputs should not be treated as substitutes for expert reading. Relevance scores, classifications, annotations, and cross-source syntheses are analytical aids that require human validation.

## Citation

Citation metadata are provided in [`CITATION.cff`](CITATION.cff). GitHub displays them through the **Cite this repository** function.

- All versions: [https://doi.org/10.5281/zenodo.24197421](https://doi.org/10.5281/zenodo.24197421)
- Version 1.0.0: [https://doi.org/10.5281/zenodo.24197422](https://doi.org/10.5281/zenodo.24197422)

## Author

Igor Kudinov — [ORCID 0000-0001-7785-1637](https://orcid.org/0000-0001-7785-1637)

## License

This project is distributed under the [MIT License](LICENSE).
