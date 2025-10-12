# Engine

in a Tab JSON, field `engine` defines default browser used when this tab gets played / opened. If the `engine` field is empty, then it'll choose `engine` field in global default.

## Launch the Browser

When the Tab JSON gets played / opened, an embedded browser thread will start, and its display appears in where your editing area is (right huge area).

Each Tab is responsible for every browser instances, so when browser crash, it's just one or few tabs that crashes, not the whole manager.