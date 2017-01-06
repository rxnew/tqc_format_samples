TQEC format samples
==============
This repository is a place for sample files in TQEC format.

Format
---------------
The following is the basic TQEC format.

```
{
    "format": "tqec",
    "circuit": {
        "bits"   : [<bit>, ...],
        "inputs" : [<external input bit>, ...],
        "outputs": [<external output bit>, ...],
        "initializations": [
            {
                "bit" : <initialization bit>,
                "type": "<initialization type>"
            }
        ],
        "measurements": [
            {
                "bit" : <measurement bit>,
                "type": "<measurement type (basis)>"
            }
        ],
        "operations": [
            {
                "type": "<operation type>",
                "bits": {
                    "controls": [<control bit>, ...],
                    "targets" : [<target bit>, ...]
                }
            }
        ],
        "modules": [
            {
                "id"      : "<module id>",
                "size"    : [<x>, <y>, <z>],
                "position": [<x>, <y>, <z>]
            }
        ]
    }
}
```

Examples of \<initialization type\> are "Z", "-Z", "X", "-X", "Y", "A", etc.  
Examples of \<operation type\> are "braiding", "P", "T", etc.
  
When describing multiple circuits in one file, write as follows.

```
{
    "format": "tqec",
    "circuits": {
        "main": {
            "modules": [
                {
                    "id"      : "cv",
                    "size"    : [10, 20, 20],
                    "position": [20, 10, 10]
                }
            ]
        },
        "cv": {
        }
    }
}
```

When describing the ICM circuit, write it as follows.

```
{
    "format": "icm",
    "circuit": {
        "bits"   : [<bit>, ...],
        "inputs" : [<external input bit>, ...],
        "outputs": [<external output bit>, ...],
        "initializations": [
            {
                "bit" : <initialization bit>,
                "type": "<initialization type>"
            }
        ],
        "measurements": [
            {
                "bit" : <measurement bit>,
                "type": "<measurement type (basis)>"
            }
        ],
        "cnots": [
            {
                "controls": [<control bit> (it must be one)],
                "targets" : [<target bit>, ...]
            }
        ]
    }
}
```
