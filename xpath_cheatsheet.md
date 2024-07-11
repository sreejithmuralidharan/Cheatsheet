# XPath Cheatsheet

## 1. Basic Syntax

XPath (XML Path Language) is a query language that allows you to navigate through elements and attributes in an XML document. Here are the basic syntax rules and expressions:

- **Node Selection:**
  - `/` : Selects the root node of the document. It is used to create an absolute path.
  - `//` : Selects nodes in the document from the current node that match the selection, regardless of their location. It is used to create a relative path.
  - `.` : Selects the current node.
  - `..` : Selects the parent of the current node.
  - `@` : Selects attributes. For example, `@id` selects the attribute with the name `id`.

- **Node Name:**
  - `nodename` : Selects all nodes with the name "nodename". For instance, `book` selects all `book` elements in the document.

## 2. Path Expressions

Path expressions are used to select nodes or node-sets in an XML document. They can be absolute or relative.

- **Absolute Path:**
  - `/html/body/div` : Selects the `div` element that is a child of the `body` element, which is itself a child of the `html` element. Absolute paths start with a `/`.

- **Relative Path:**
  - `//div` : Selects all `div` elements in the document, no matter where they are.
  - `div/p` : Selects all `p` elements that are children of any `div` element. Relative paths do not start with a `/`.

## 3. Predicates

Predicates are used to find a specific node or a node that contains a specific value. They are enclosed in square brackets.

- **Basic Predicates:**
  - `//div[@id='main']` : Selects all `div` elements with `id="main"`.
  - `//div[@class='test']` : Selects all `div` elements with `class="test"`.
  - `//div[1]` : Selects the first `div` element. Indexing starts at 1.
  - `//div[last()]` : Selects the last `div` element.
  - `//div[position()<3]` : Selects the first and second `div` elements (positions less than 3).

- **Compound Predicates:**
  - `//div[@class='test' and @id='main']` : Selects all `div` elements with both `class="test"` and `id="main"`.
  - `//div[@class='test' or @id='main']` : Selects all `div` elements with either `class="test"` or `id="main"`.

## 4. Axes

Axes are used to define the node-set relative to the current node. Here are some commonly used axes:

- **Child:**
  - `child::div` : Selects all `div` children of the current node. In abbreviated syntax, this is equivalent to `div`.

- **Descendant:**
  - `descendant::div` : Selects all `div` descendants of the current node. In abbreviated syntax, this is equivalent to `//div`.

- **Parent:**
  - `parent::node()` : Selects the parent of the current node. In abbreviated syntax, this is equivalent to `..`.

- **Following Sibling:**
  - `following-sibling::div` : Selects all `div` siblings after the current node.

- **Preceding Sibling:**
  - `preceding-sibling::div` : Selects all `div` siblings before the current node.

- **Ancestor:**
  - `ancestor::div` : Selects all `div` ancestors of the current node.

- **Following:**
  - `following::div` : Selects everything in the document after the closing tag of the current node.

- **Preceding:**
  - `preceding::div` : Selects all nodes that appear before the current node in the document.

## 5. Functions

XPath functions provide powerful capabilities to select nodes based on their values and positions.

- **Text Functions:**
  - `text()` : Selects the text content of the current node.
  - `contains(text(), 'value')` : Selects nodes where the text contains the specified value. For example, `//div[contains(text(), 'example')]` selects all `div` elements containing the text "example".
  - `starts-with(text(), 'value')` : Selects nodes where the text starts with the specified value. For example, `//div[starts-with(text(), 'example')]` selects all `div` elements where the text starts with "example".

- **Position Functions:**
  - `position()` : Selects the position of a node in the node-set. For example, `//div[position()=2]` selects the second `div` element.
  - `last()` : Selects the last position of a node in the node-set. For example, `//div[last()]` selects the last `div` element.

- **Node Set Functions:**
  - `count(node)` : Counts the number of nodes in a node-set. For example, `count(//div)` returns the number of `div` elements.
  - `name(node)` : Returns the name of the node. For example, `name(//div)` returns "div".

## 6. Wildcards

Wildcards are used to select unknown or variable nodes and attributes.

- **Element Wildcard:**
  - `*` : Selects all elements. For example, `/html/body/*` selects all child elements of the `body` element.
  - `div/*` : Selects all child elements of any `div`.

- **Attribute Wildcard:**
  - `@*` : Selects all attributes. For example, `//@*` selects all attributes in the document.

## 7. Combining Expressions

Expressions can be combined using various operators to create complex queries.

- **Union:**
  - `//div | //span` : Selects all `div` and `span` elements.

- **Grouping:**
  - `//div[@class='test' or @id='main']` : Selects all `div` elements with either `class="test"` or `id="main"`.

## Examples

Here are a few examples to illustrate the use of XPath:

1. **Selecting Elements by Attribute:**
   `//input[@type='text']` This selects all input elements where the type attribute is equal to "text".

2. **Selecting Elements by Text Content:**
  `//a[text()='Home']` This selects all a (anchor) elements with the exact text content "Home".

3. **Selecting Elements by Partial Attribute Value:**
  `//div[contains(@class, 'header')]` This selects all div elements with a class attribute that contains the text "header".

4. **Selecting the N-th Element:**
  `(//ul/li)[3]` This selects the third li element in all ul elements.

5. **Selecting Based on Multiple Conditions:**
  `//input[@type='text' and @name='username']` This selects all input elements where type is "text" and name is "username".



