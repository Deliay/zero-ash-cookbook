# Product Document Specification

Product documents are typically placed in the `docs/product` directory and must follow [[document-workflow.md]]. **Technical details are strictly prohibited** in product documents, including project structure, frontend structure, frontend components, backend API design, etc.

## Product Document Management

Product document lifecycle is divided into three categories, corresponding to different directories:

- `docs/product/draft` - Draft product documents; all new product documents go here
- `docs/product/reviewed` - Product documents that have passed review
- `docs/product/shipping` - Product documents ready for implementation
- `docs/product/released` - Product documents that have been accepted and successfully launched

### Create Product Document

USE FOR: create a new product document
REFERENCE: [[git.md]], [[prd/create-prd.md]]

### Edit Product Document

USE FOR: update a draft product document
REFERENCE: [[git.md]], [[prd/edit-prd.md]]

### Publish Product Document

USE FOR: when some product documents user approved or reviewed
REFERENCE: [[git.md]], [[prd/reviewed-prd.md]]

## Product Document Structure Template

Load content from [[prd/product-document-template.md]] and fill in accordingly. Product documents should be rich in visuals, using Mermaid diagrams alongside text.