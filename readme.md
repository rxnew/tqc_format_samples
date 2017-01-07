TQC format samples
==============
This repository is a place for sample files in TQC format.

Format
---------------
The following is the basic QC (Quantum Circuit) format.

```
{
    "format": "qc",
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
        "gates": [
            {
                "type": "<gate type>",
                "controls": [<control bit>, ...],
                "targets" : [<target bit>, ...]
            }, ...
        ]
    }
}
```

Examples of \<initialization type\> are "z", "-z", "x", "-x", "y", "a", etc.  
Examples of \<measurement type\> are "z", "x", "z/x", etc.  
Examples of \<gate type\> are "x", "p", "t", etc.
  
The following is the basic ICPM (Initialization Cnot Pin Measurement) format.

```
{
    "format": "icpm",
    "circuits": {
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
                "type"    : "cnot",
                "controls": [<control bit>  (it must be one)],
                "targets" : [<target bit>]
            },
            {
                "type"    : "pin",
                "module"  : "<connected module id>",
                "controls": [<control bit>],
                "targets" : [<target bit>]
            }, ...
        ]
    }
}
```

The operations other than cnot and Pauli gate correspond to pins.
  
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
