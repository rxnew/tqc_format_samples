TQEC format samples
==============
This repository is a place for sample files in TQC format.

Format
---------------
The following is the basic ICPM (Initialization Cnot Pin Measurement) format.

```
{
    "format": "icpm",
    "circuit": {
        "bits"   : [<bit>, ...],
        "inputs" : [<external input bit>, ...],
        "outputs": [<external output bit>, ...],
        "initializations": [
            {
                "bit" : <initialization bit>,
                "type": "<initialization type>"
            }, ...
        ],
        "measurements": [
            {
                "bit" : <measurement bit>,
                "type": "<measurement type (basis)>"
            }, ...
        ],
        "operations": [
            {
                "type": "<operation type>",
                "bits": {
                    "controls": [<control bit>, ...],
                    "targets" : [<target bit>, ...]
                }
            }, ...
        ],
        "modules": [
            {
                "id"    : "<module circuit id>",
                "size"  : [<x>, <y>, <z>],
                "number": <number of the module template>
            }, ...
        ]
    }
}
```

Examples of \<initialization type\> are "Z", "-Z", "X", "-X", "Y", "A", etc.  
Examples of \<operation type\> are "CNOT", "P", "T", etc.
Gates other than CNOT correspond to pins.
  
When describing multiple circuits in one file, write as follows.

```
{
    "format": "icpm",
    "circuits": {
        "main": {
            "modules": [
                {
                    "id"    : "cv",
                    "size"  : [10, 20, 20],
                    "number": 1
                }
            ]
        },
        "cv": {
        }
    }
}
```

When describing the ICM (Initialization Cnot Measurement) circuit, write it as follows.

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
            }, ...
        ],
        "measurements": [
            {
                "bit" : <measurement bit>,
                "type": "<measurement type (basis)>"
            }, ...
        ],
        "cnots": [
            {
                "controls": [<control bit> (it must be one)],
                "targets" : [<target bit>, ...]
            }, ...
        ]
    }
}
```

When describing the TQEC (Topologically Quantum Error Corrected) geometory circuit, write it as follows.

```
{
    "format": "tqec",
    "circuit": {
        "logical_qubits": [
            {
                "id": <logical qubit id>,
                "type": "<rough or smooth>",
                "blocks": [
                    [[<x>, <y>, <z>], ...], ...
                ],
                "injectors": [
                    [[<x>, <y>, <z>], ...], ...
                ]
                "caps": [
                    [[<x>, <y>, <z>], ...], ...
                ]
            }, ...
        ],
        "modules": [
            {
                "id"      : "<module circuit id>",
                "size"    : [<x>, <y>, <z>],
                "position": [<x>, <y>, <z>],
                "rotation": [<axis>, <axis>, <axis>]
            }, ...
        ]
    }
}
```
