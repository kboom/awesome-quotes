# Practical

## Encoding

1. There always is a schema. Either on write (classic) or on read (so-called schemaless).
1. Keeping a database of schemas allows you to check forward and backward com‐ patibility of schema changes, before anything is deployed.
2. For users of statically typed programming languages, the ability to generate code from the schema is useful, since it enables type checking at compile time.
3. The schema is a valuable form of documentation, and because the schema is required for decoding, you can be sure that it is up to date (whereas manually maintained documentation may easily diverge from reality). 