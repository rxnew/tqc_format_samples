TQC format samples
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
        ]
    }
}
```

Examples of \<initialization type\> are "Z", "-Z", "X", "-X", "Y", "A", etc.  
Examples of \<operation type\> are "cnot", "x", "p", "t", etc.
The operations other than cnot and Pauli operation correspond to pins, and the operation name corresponds to the module circuit id.
  
When describing multiple circuits in one file, write as follows.

```
{
    "format": "icpm",
    "circuits": {
        "main": {
            "operations": [
                {
                    "type": "cv",
                    "bits": {
                        "controls": [<control bit>],
                        "targets" : [<target bit>]
                    }
                }, ...
            ], ...
        },
        "cv": {
            ...
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
        ],
        "pauli_products": [
            {
                "bit" : <target bit>,
                "type": "<pauli product>"
            }, ...
        ]
    }
}
```

Examples of \<pauli product\> are "x", "z", "xz", etc.
  
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
