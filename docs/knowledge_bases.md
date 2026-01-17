# Knowledge Bases

Create and manage knowledge bases and documents.

## List knowledge bases

- Method: GET
- Path: `/v2/knowledge-bases`

### Parameters

- `page_size` (integer, optional): 1-100. Default: 20.
- `page_token` (string, optional): Pagination token.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
items = client.knowledge_bases.list(page_size=20)
```

## Create knowledge base

- Method: POST
- Path: `/v2/knowledge-bases`

### Parameters

- `name` (string, required): Unique name for the knowledge base.
- `description` (string, required): What this knowledge base contains.
- `document_language` (string, optional): Default document language. Default `en`.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "name": "Company Policies",
    "description": "Internal policies and procedures",
    "document_language": "en",
}
kb = client.knowledge_bases.create(payload)
```

## Get knowledge base

- Method: GET
- Path: `/v2/knowledge-bases/{kb_id}`

### Parameters

- `kb_id` (string, required): Knowledge base ID.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
kb = client.knowledge_bases.get("kb_id")
```

## Update knowledge base

- Method: PUT
- Path: `/v2/knowledge-bases/{kb_id}`

### Parameters

- `name` (string, optional): New name.
- `description` (string, optional): New description.
- `document_language` (string, optional): New default language.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
updated = client.knowledge_bases.update("kb_id", {"description": "Updated scope"})
```

## Delete knowledge base

- Method: DELETE
- Path: `/v2/knowledge-bases/{kb_id}`

### Parameters

- `kb_id` (string, required): Knowledge base ID.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
client.knowledge_bases.delete("kb_id")
```

## Fetch website sitemap

Discover URLs from a website for ingestion.

- Method: POST
- Path: `/v2/knowledge-bases/website/sitemap`

### Parameters

- `url` (string, required): Base website URL.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
sitemap = client.knowledge_bases.fetch_website_sitemap("https://example.com")
```

## Add website documents

Add website pages to a knowledge base.

- Method: POST
- Path: `/v2/knowledge-bases/{kb_id}/documents/website`

### Parameters

- `base_url` (string, required): Base URL of the website.
- `selected_sitemap_urls` (list[string], required): Specific URLs to crawl.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "base_url": "https://example.com",
    "selected_sitemap_urls": ["https://example.com/docs"],
}
result = client.knowledge_bases.add_website_documents("kb_id", payload)
```

## Add file documents

Upload files to a knowledge base.

- Method: POST
- Path: `/v2/knowledge-bases/{kb_id}/documents/files`

### Parameters

- `files` (file[], required): Files to upload.
- `document_languages` (list[string], optional): Languages for each document.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
with open("policy.pdf", "rb") as handle:
    files = [("files.items", ("policy.pdf", handle))]
    result = client.knowledge_bases.add_files_documents("kb_id", files, ["en"])
```

## Check document status

- Method: GET
- Path: `/v2/knowledge-bases/{kb_id}/documents/{document_id}/status`

### Parameters

- `kb_id` (string, required): Knowledge base ID.
- `document_id` (string, required): Document ID.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
status = client.knowledge_bases.get_document_status("kb_id", "document_id")
```

## Delete document

- Method: DELETE
- Path: `/v2/knowledge-bases/{kb_id}/documents/{document_id}`

### Parameters

- `kb_id` (string, required): Knowledge base ID.
- `document_id` (string, required): Document ID.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
client.knowledge_bases.delete_document("kb_id", "document_id")
```

## List documents

- Method: GET
- Path: `/v2/knowledge-bases/{kb_id}/documents`

### Parameters

- `page_size` (integer, optional): 1-100. Default: 20.
- `page_token` (string, optional): Pagination token.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
docs = client.knowledge_bases.list_documents("kb_id", page_size=20)
```
