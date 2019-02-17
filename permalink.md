---
permalink: /foo/bar/
---

# permalink.md 

- `filename`:  permalink.md
- `permalink`: /foo/bar/

## From permalink page to normal page

- **Source**:

  ```markdown
  [Go to `(./normal.md)`](./normal.md)
  ```

- **Output**:

  [Go to `(./normal.md)`](./normal.md)


## From permalink page to permalink page

- **Source**:

  ```markdown
  [Go to `(./foo/bar/permalink.md)`](./foo/bar/permalink.md)
  ```

- **Output**:

  [Go to `(./foo/bar/permalink.md)`](./foo/bar/permalink.md)

