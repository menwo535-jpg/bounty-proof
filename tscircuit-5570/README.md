Tested against core 5d9e4a0630bebe77003ee31e0dfa5993ee22e394 and schematic-symbols 72745d3a3362e2bf3ca4b2dcd6f720d1584f1175.

Apply bidirectional-tvs.patch to schematic-symbols and build it. Apply core-tvs.patch to core. The new schematic test exercises both TVS prop forms, a rotated bidirectional part, an explicitly unidirectional part, a standard diode and a Zener diode.

Both core and its SVG renderer need to resolve the patched symbols package. In this checkout circuit-to-svg@0.0.460 resolved its own nested schematic-symbols. Updating just core produced the expected symbol names in circuit JSON but the diagram said “Symbol not found”. With the same local symbols build resolved from both packages, each bidirectional part produced seven SVG paths. The released dependencies still need to pick up the symbol upstream.

With that dependency setup, run `bun test tests/components/normal-components/diode-tvs-symbol.test.tsx`. The full eight diode test files passed (10 tests and 160 assertions). The independent symbol-library suite passed 41 tests. `core-circuit.png` is the rendered test circuit.
