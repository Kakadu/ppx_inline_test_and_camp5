Calling

    dune clean && dune build lib ./rewriter.exe ./rewriter_p5.exe --verbose -j1

Successfully compiles `rewriter.exe` but fails on `rewriter_p5.exe`.
By some reason library `lib/lib1.cmxa` depends on runtime lib of `ppx_inline_test`,
i.e. dune expands macroses that testing code got into a library. What did I do wrong?
