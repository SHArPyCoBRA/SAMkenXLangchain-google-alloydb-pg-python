# AlloyDB for PostgreSQL for LangChain

This package contains the [LangChain][langchain] integrations for AlloyDB for PostgreSQL.

> **🧪 Preview:** This feature is covered by the Pre-GA Offerings Terms of the Google Cloud Terms of Service. Please note that pre-GA products and features might have limited support, and changes to pre-GA products and features might not be compatible with other pre-GA versions. For more information, see the [launch stage descriptions](https://cloud.google.com/products#product-launch-stages)

* [Documentation][docs]
* [API Reference]()

## Getting Started

In order to use this library, you first need to go through the following steps:

1. [Select or create a Cloud Platform project.][project]
2. [Enable billing for your project.][billing]
3. [Enable the Google Cloud AlloyDB API.][api]
4. [Setup Authentication.][auth]

### Installation

Install this library in a [`virtualenv`][venv] using pip. [`virtualenv`][venv] is a tool to
create isolated Python environments. The basic problem it addresses is one of
dependencies and versions, and indirectly permissions.

With [`virtualenv`][venv], it's possible to install this library without needing system
install permissions, and without clashing with the installed system
dependencies.

```bash
pip install virtualenv
virtualenv <your-env>
source <your-env>/bin/activate
<your-env>/bin/pip install langchain-google-alloydb-pg
```

## Vector Store Usage

Use a vector store to store embedded data and perform vector search.

```python
from langchain_google_alloydb_pg import AlloyDBEngine, AlloyDBVectorstore
from langchain_google_vertexai import VertexAIEmbeddings


engine = AlloyDBEngine.from_instance("project-id", "region", "my-cluster", "my-instance", "my-database")
embeddings_service = VertexAIEmbeddings()
vectorstore = AlloyDBVectorStore(
    engine,
    table_name="my-table",
    embeddings=embedding_service
)
```

See the full [Vector Store][vectorstore] tutorial.

## Document Loader Usage

Use a document loader to load data as LangChain `Document`s.

```python
from langchain_google_alloydb_pg import AlloyDBEngine, AlloyDBLoader


engine = AlloyDBEngine.from_instance("project-id", "region", "my-cluster", "my-instance", "my-database")
loader = PostgresSQLLoader(
    engine,
    table_name="my-table-name"
)
docs = loader.lazy_load()
```

See the full [Document Loader][loader] tutorial.

## Chat Message History Usage

Use `ChatMessageHistory` to store messages and provide conversation history to LLMs.

```python
from langchain_google_alloydb_pg import AlloyDBChatMessageHistory, AlloyDBEngine


engine = AlloyDBEngine.from_instance("project-id", "region", "my-cluster", "my-instance", "my-database")
history = AlloyDBChatMessageHistory(
    engine,
    table_name="my-message-store",
    session_id="my-session-id"
)
```

See the full [Chat Message History][history] tutorial.

## Contributing

Contributions to this library are always welcome and highly encouraged.

See [CONTRIBUTING][contributing] for more information how to get started.

Please note that this project is released with a Contributor Code of Conduct. By participating in
this project you agree to abide by its terms. See [Code of Conduct][coc] for more
information.

## License

Apache 2.0 - See [LICENSE][license] for more information.

## Disclaimer

This is not an officially supported Google product.

[project]: https://console.cloud.google.com/project
[billing]: https://cloud.google.com/billing/docs/how-to/modify-project#enable_billing_for_a_project
[api]: https://console.cloud.google.com/flows/enableapi?apiid=alloydb.googleapis.com
[auth]: https://googleapis.dev/python/google-api-core/latest/auth.html
[venv]: https://virtualenv.pypa.io/en/latest/
[loader]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/docs/document_loader.ipynb
[vectorstore]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/docs/vector_store.ipynb
[history]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/docs/chat_message_history.ipynb
[langchain]: https://github.com/langchain-ai/langchain
[docs]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/docs
[license]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/LICENSE
[contributing]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/CONTRIBUTING.md
[coc]: https://github.com/googleapis/langchain-google-alloydb-pg-python/tree/main/CODE_OF_CONDUCT.md
