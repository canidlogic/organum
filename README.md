# Organum

A pedal shader for NMF files.

Organum is able to apply musical effects that simulate the sustain pedal on a piano.  Organum is also able to transform grace notes into regular notes.  The syntax of the organum program is as follows:

    organum [pedal_map] [pedal_shader] < [input] > [output]

The `[pedal_map]` parameter is the path to a pedal map file.  This is a [Shastina](https://www.purl.org/canidtech/r/shastina) script that defines zero or more pedal maps, each of which describes when the virtual sustain pedal is down, up, and refreshed.  See the `pedal_map.txt` file in the `doc` directory for the syntax of the script.

The `[pedal_shader]` parameter is the path to a Lua script that serves as the pedal shader.  This shader determines which notes in the input NMF file are affected by which pedal map.  See the `PedalShader.md` file in the `doc` directory for more information.

Standard `[input]` to the program should be an [NMF](https://www.purl.org/canidtech/r/libnmf) file to transform according to the pedal shaders.  There are no restrictions on the kind of NMF file that can be passed to Organum.

Standard `[output]` from the program is an NMF file that has been transformed according to the pedal shaders.  It will have the same quantum basis as the input NMF file.  All notes and cues will be passed through unchanged from the input NMF file, except for the following transformations:

1. Grace notes may be transformed into regular notes.
2. Notes affected by pedal maps may have their durations adjusted.

## Compilation

Organum must be compiled with:

- [liblua](https://www.lua.org/) version 5.4
- [Shastina](https://www.purl.org/canidtech/r/shastina) beta 0.9.3 or compatible
- [libnmf](https://www.purl.org/canidtech/r/libnmf) beta 0.9.0 or compatible

The math library may also be required with `-lm`
