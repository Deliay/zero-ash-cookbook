# 产品文档规范

产品文档一般放置在`docs/product`文件夹中，产品文档也遵照 [[document-standards.md]] 来输出。产品文档中禁止提及技术细节，**禁止提及项目结构、前端结构、前端组件、后端API设计等内容**

## 产品文档管理

将产品文档生命周期分为三类，对应不同文件夹

- `docs/product/draft` 存放产品文档草稿，新建的产品文档一律放入此文件夹
- `docs/product/reviewed` 通过Review的产品文档
- `docs/product/shipping` 开始实现的的产品文档
- `docs/product/released` 已经通过产品验收，成功上线的产品文档

### 创建产品文档

USE FOR: create a new product document
REFERENCE: [[git.md]], [[prd/create-prd.md]]

### 修改产品文档

USE FOR: update a draft product document
REFERENCE: [[git.md]], [[prd/edit-prd.md]]

### 公布产品文档

USE FOR: when some product documents user approved or reviewed
REFERENCE: [[git.md]], [[prd/reviewed-prd.md]]

## 产品文档结构模板

加载[[prd/product-document-template.md]]的内容并填写。产品文档内容应该图文并茂，使用mermdia diagram与文字并行编写。
