TQEC format samples
==============
This repository is ~.

Format
---------------
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
                "type": "<operation_type>",
                "bits": {
                    "controls": [<control bit>, ...]
                    "targets" : [<target bit>, ...]
                }
            }
        ],
        "modules": [
            {
               "id"     : "<module_id>",
                "size"  : [<x>, <y>, <z>],
                "number": <number of modules>
            }
        ]
    }
}
```
