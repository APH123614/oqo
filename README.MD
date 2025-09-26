# OQO – Open‑Quote Object

OQO (“Open‑Quote Object”) is a lightweight, open specification for representing quotes and proposals as structured JSON.  The goal is to make it easy for contractors, suppliers and clients to exchange quote information in a consistent format without locking themselves into a particular vendor or proprietary system.  By publishing the schema and providing sample data and validation tools, we hope to encourage interoperability and adoption across construction, procurement, and service industries.

This repository contains the core JSON schema, a sample quote and a handful of tooling to get you started.  There is no application code here – just the specification and supporting artefacts.  Feel free to fork the project, file issues or propose changes via pull request.

## 📘 Specification

The current version of the OQO schema lives in the `open-schema` folder of this repository.  It describes the structure of a quote object using the JSON Schema 2020‑12 dialect.  A hosted, human‑friendly version of the schema will also be available on our website:

pgsql
Copy code
https://tibr.ai/open-schema/oqo.json
pgsql
Copy code

If you’re new to JSON Schema, check out JSON Schema – Getting Started for an overview of the key concepts.

## 🧾 Example

The `sample_quote.json` file illustrates a minimal yet realistic quote using the OQO format.  Each quote includes an identifier, issuer and client information, an array of line items (with quantities and unit prices), currency, totals and dates.  You can modify this file and validate it with the provided validator script (see below).

```json
{
  "quoteId": "Q0123",
  "issuer": {
    "name": "Acme Construction Ltd.",
    "address": "1234 Elm Street, Montreal, QC, Canada",
    "contactEmail": "sales@acmeconstruction.com"
  },
  "client": {
    "name": "Sunrise Realty Inc.",
    "address": "456 Maple Avenue, Ottawa, ON, Canada",
    "contactEmail": "projects@sunriserealty.ca"
  },
  "items": [
    {
      "description": "Site survey and inspection",
      "quantity": 1,
      "unitPrice": 1500.00,
      "lineTotal": 1500.00
    },
    {
      "description": "Architectural design work",
      "quantity": 1,
      "unitPrice": 8000.00,
      "lineTotal": 8000.00
    },
    {
      "description": "Project management",
      "quantity": 40,
      "unitPrice": 75.00,
      "lineTotal": 3000.00
    }
  ],
  "currency": "CAD",
  "totalAmount": 12500.00,
  "issueDate": "2025-09-25",
  "expirationDate": "2025-11-25",
  "status": "Draft",
  "notes": "This quote is valid for 60 days from the issue date."
}
🚀 Getting Started
To work with the schema and sample data locally:

Clone this repository.

Ensure you have Python 3 installed.

Install the optional dependencies (for validation):

nginx
Copy code
pip install jsonschema
Run the validator script against the sample quote:

pgsql
Copy code
python tools/validate_quote.py sample_quote.json open-schema/oqo.json
Explore the sample_quotes.csv file and accompanying Jupyter notebook in the datasets folder to see how anonymised quotes can be published for analysis.

🔧 Tools
This repository includes a few helper scripts to make working with OQO easier:

tools/validate_quote.py – A simple Python script that validates a JSON document against the OQO schema and reports any errors.

tools/validate_quote.js – A browser‑friendly JavaScript validator using Ajv. You can embed this in your own projects or in the demo page.

datasets/sample_quotes.csv – 100 anonymised sample quotes for testing and demonstration purposes.

notebooks/sample_quotes_demo.ipynb – A Jupyter notebook that loads the CSV and previews the data.

🤝 Contributing
We welcome contributions! Please open an issue to discuss enhancements or questions. When submitting a pull request, follow the existing coding conventions and include tests if you add new functionality.

📝 License
This project is licensed under the MIT license. See the LICENSE file for details.

📬 Contact
## About TIBR

OQO is part of the **TIBR growth campaign**, an initiative to modernise estimating and quoting workflows in the construction and services industries. To learn more about TIBR’s estimating software and services, visit [tibr.com](https://tibr.com).

For questions or commercial enquiries, please contact Team OQO at support@tibr.tech.
## Datasets

## Datasets

- [Standardized Quote Dataset – JSON Schema (TIBR)](https://www.kaggle.com/datasets/drandrewharris/standardized-quote-dataset-json-schema-tibr)


