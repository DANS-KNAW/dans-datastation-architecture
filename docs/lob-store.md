Large Object Store
==================

The large object-store (LOB-store) for a [Data Vault Storage Root](data-vault-storage-root.md) contains any files that cause a Dataset Version Export to be
larger than the configured maximum size. Note that this means that these files may be smaller than 1G by themselves.

Conceptually, the LOB-store is a key-value store with:

* key: the SHA-1 digest of the object
* value: the file data

Structure
---------
The structure of the LOB-store is as simple as possible. Its main purpose is to preserve the objects stored in an easy-to-understand manner.

```text
.
└── store.lobs
    └── <bucket>.dmftar
        └── 0000
            ├── <bucket>.dmftar.tar
            ├── <bucket>.dmftar.tar.chksum
            └── <bucket>.dmftar.tar.idx

```

A bucket may contain one or more files. The name of a bucket is a UUID in hexadecimal. To avoid problems with the filesystem or tools, the name is split over
two directory-levels, with the first two characters forming the name of the first level, e.g.,

```text 
archive/data-vault/archaeology.lobs
├── ab
│   └── a954c1-94bf-4daa-896b-203973153904
│        ....
└── d1
    └── a86859-d0e9-4aaa-874d-7659828c8b1b
        └── d1a86859-d0e9-4aaa-874d-7659828c8b1b.dmftar
            └── 0000
                ├── d1a86859-d0e9-4aaa-874d-7659828c8b1b.tar
                ├── d1a86859-d0e9-4aaa-874d-7659828c8b1b.tar.chksum
                └── d1a86859-d0e9-4aaa-874d-7659828c8b1b.tar.idx

```

Retrieving an object
--------------------

The name of each file is its SHA-1 digest. To look up a file, scan all the .idx files in the LOB-store for a matching file name after `./`. You can then extract
the file with:

```text
dmftar -x -f store.lobs/<bucket>.dmftar `./<sha1>` 
```

e.g.,

```bash
dmftar -x -f \
   archive/data-vault/archaeology.lobs/d1/a86859-d0e9-4aaa-874d-7659828c8b1b/d1a86859-d0e9-4aaa-874d-7659828c8b1b.dmftar \
     ./3f24c343d7e7e1d8606c894689625de5a53df28c
```

!!! alert "Increasing look-up speed"

    If you need to restore a lot of objects from the Data Vault Store Root, you will likely need to be able to look up large objects quickly. In that case it is
    recommended that you build a look-up table from SHA-1 to bucket containing the file. Note that dd-lob-store maintains such a look-up table in its database.