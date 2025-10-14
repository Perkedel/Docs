# Mirror

A special tab file mode that allows you to mirror other tab files. Much simpler than Filesystem linkings

Simply use protocol `htbrowsermirror://` in the URL, and fill the rest with where your tab file path is

```json
{
    "title": "Modified name mirror",
    "url": "htbrowsermirror://Test/example.json",
}
```

You can then put this mirror anywhere you'd like.

Example use case if there is an electronic project that provides the coding & its STL case at the same time. Therefore, you will have 2 topic spaces at the same time: `Arduino` & `3D Models`. You can start from either of those, let's say `Arduino`. Create a split about its STL file. Now, you can create mirror of this Tab file at `3D Models` space, to make double reminder.