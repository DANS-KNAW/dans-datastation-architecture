Deposit directory
=================

A _deposit directory_ is a directory containing:

1. a deposit
2. deposit properties

```text
.
└── deposit-directory
    ├── <deposit files>
    └── deposit.properties
```

`<deposit files>`
-----------------
The deposit files are one or more files or directories. Typically, it will be one directory, a [bag]{:target=_blank}, and more specifically, one
conforming to the [DANS BagIt Profile v1]{:target=_blank}. However, applications have different requirements with respect to the contents and lay-out of the
deposit.

`deposit.properties`
--------------------
Processing metadata about the deposit are stored in a [properties file]{:target=_blank} called `deposit.properties`.

It shall have at minimum the following properties:

| Key                   | Format                                                         | Description                                                                                                  |
|-----------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| `creation.timestamp`  | ISO 8601 datetime, <br/>including timezone and in ms precision | Date/time when the deposit<br/> directory was created                                                        |
| `state.label`         |                                                                | A label indicating the current<br/> state of the deposit                                                     |
| `state.description`   |                                                                | A human readable description of <br/>the state or an error message, <br/>if `state.label` indicates an error | 

Applications may use additional properties.


[bag]: https://tools.ietf.org/html/rfc8493
[DANS BagIt Profile v1]: {{ dans_bagit_profile }}
[properties file]: https://en.wikipedia.org/wiki/.properties
