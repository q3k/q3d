q3d - a boneless 3d object format for asset exchange
====================================================

Current Stability: **will break backwards compatibility**

q3d is what you should want to use if you want your application to export/import simple 3d meshes.

It only supports triangle-based meshes. There is no support for NURBS surfaces, Bezier curves, ... It is not meant to be a primary format of storage for a 3d modelling program, or to represent parametric geometry. Instead, it should be used for 'baked' assets, for instance in games, CAM or CAD assembly.

It's based on [FlatBuffers](https://google.github.io/flatbuffers/), so you get importers/exporters for 'free' in at least the following programming languages:
 - C
 - C++
 - C#
 - Go
 - Java
 - Lua
 - Python
 - Rust

Capabilities
------------

Currently we ship the spec for a 'q3d object' (`q3do`) file format. This format defines a single Object, that in turn contains multiple Meshes, each Mesh being made up of a list of Triangles and a Material.

For more information, see `object.fbs`.

Why not..?
----------

Other file format?

 - STL: proprietary, no canonical colour support
 - STEP: designed by a committee, closed ISO spec
 - OBJ/MTL: split files for object and material data, complex feature set
 - AMF: designed by a drunk committee, closed ISO spec
 - COLLADA: designed by a batshit insane committee
 - PLY: underspecified

Features?

 - Units other than millimeters: No.

Future development
------------------

 - Textured triangles

License
-------

This entire repository (including the specification, documentation and example code) is licensed under CC0, which means you are free to use it as if it were public domain.

Usage
=====

First, read the specification IDL (`object.fbs`).

You will need FlatBuffers-the-library-for-your language, and FlatBuffers-the-flatc-compiler.

See the [FlatBuffers website](https://google.github.io/flatbuffers/flatbuffers_guide_building.html) for more information on how to use FlatBuffers.
