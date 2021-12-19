Calling

    dune clean && dune build lib ./rewriter.exe ./rewriter_p5.exe --verbose -j1

Successfully compiles `rewriter.exe` but fails on `rewriter_p5.exe`.
By some reason library `lib/lib1.cmxa` depends on runtime lib of `ppx_inline_test`,
i.e. dune expands macroses that testing code got into a library. What did I do wrong?


````
➜  inline_test-hack git:(master) dune clean && dune build lib ./rewriter.exe ./rewriter_p5.exe --verbose -j1
Workspace root: /media/work/asp/inline_test-hack
disable binary cache
Running[0]: /media/work/.opam/4.12.1+flambda/bin/ocamlc.opt -config > /tmp/duneba0f54.output
Dune context:
 { name = "default"
 ; kind = "default"
 ; profile = Dyn
 ; merlin = true
 ; for_host = None
 ; fdo_target_exe = None
 ; build_dir = "default"
 ; toplevel_path =
     Some External "/media/work/.opam/4.12.1+flambda/lib/toplevel"
 ; ocaml_bin = External "/media/work/.opam/4.12.1+flambda/bin"
 ; ocaml = Ok External "/media/work/.opam/4.12.1+flambda/bin/ocaml"
 ; ocamlc = External "/media/work/.opam/4.12.1+flambda/bin/ocamlc.opt"
 ; ocamlopt = Ok External "/media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt"
 ; ocamldep = Ok External "/media/work/.opam/4.12.1+flambda/bin/ocamldep.opt"
 ; ocamlmklib =
     Ok External "/media/work/.opam/4.12.1+flambda/bin/ocamlmklib.opt"
 ; env =
     map
       { "DUNE_OCAML_HARDCODED" : "/media/work/.opam/4.12.1+flambda/lib"
       ; "DUNE_OCAML_STDLIB" : "/media/work/.opam/4.12.1+flambda/lib/ocaml"
       ; "DUNE_SOURCEROOT" : "/media/work/asp/inline_test-hack"
       ; "INSIDE_DUNE" : "/media/work/asp/inline_test-hack/_build/default"
       ; "OCAMLFIND_IGNORE_DUPS_IN" :
           "/media/work/asp/inline_test-hack/_build/install/default/lib"
       ; "OCAMLPATH" :
           "/media/work/asp/inline_test-hack/_build/install/default/lib"
       ; "OCAMLTOP_INCLUDE_PATH" :
           "/media/work/asp/inline_test-hack/_build/install/default/lib/toplevel"
       ; "OCAML_COLOR" : "always"
       ; "OPAMCOLOR" : "always"
       }
 ; findlib_path = [ External "/media/work/.opam/4.12.1+flambda/lib" ]
 ; arch_sixtyfour = true
 ; natdynlink_supported = true
 ; supports_shared_libraries = true
 ; ocaml_config =
     { version = "4.12.1"
     ; standard_library_default =
         "/media/work/.opam/4.12.1+flambda/lib/ocaml"
     ; standard_library = "/media/work/.opam/4.12.1+flambda/lib/ocaml"
     ; standard_runtime = "the_standard_runtime_variable_was_deleted"
     ; ccomp_type = "cc"
     ; c_compiler = "gcc"
     ; ocamlc_cflags = [ "-O2"; "-fno-strict-aliasing"; "-fwrapv"; "-fPIC" ]
     ; ocamlc_cppflags = [ "-D_FILE_OFFSET_BITS=64"; "-D_REENTRANT" ]
     ; ocamlopt_cflags =
         [ "-O2"; "-fno-strict-aliasing"; "-fwrapv"; "-fPIC" ]
     ; ocamlopt_cppflags = [ "-D_FILE_OFFSET_BITS=64"; "-D_REENTRANT" ]
     ; bytecomp_c_compiler =
         [ "gcc"
         ; "-O2"
         ; "-fno-strict-aliasing"
         ; "-fwrapv"
         ; "-fPIC"
         ; "-D_FILE_OFFSET_BITS=64"
         ; "-D_REENTRANT"
         ]
     ; bytecomp_c_libraries = [ "-lm"; "-ldl"; "-lpthread" ]
     ; native_c_compiler =
         [ "gcc"
         ; "-O2"
         ; "-fno-strict-aliasing"
         ; "-fwrapv"
         ; "-fPIC"
         ; "-D_FILE_OFFSET_BITS=64"
         ; "-D_REENTRANT"
         ]
     ; native_c_libraries = [ "-lm"; "-ldl" ]
     ; cc_profile = []
     ; architecture = "amd64"
     ; model = "default"
     ; int_size = 63
     ; word_size = 64
     ; system = "linux"
     ; asm = [ "as" ]
     ; asm_cfi_supported = true
     ; with_frame_pointers = false
     ; ext_exe = ""
     ; ext_obj = ".o"
     ; ext_asm = ".s"
     ; ext_lib = ".a"
     ; ext_dll = ".so"
     ; os_type = "Unix"
     ; default_executable_name = "a.out"
     ; systhread_supported = true
     ; host = "x86_64-pc-linux-gnu"
     ; target = "x86_64-pc-linux-gnu"
     ; profiling = false
     ; flambda = true
     ; spacetime = false
     ; safe_string = true
     ; exec_magic_number = "Caml1999X029"
     ; cmi_magic_number = "Caml1999I029"
     ; cmo_magic_number = "Caml1999O029"
     ; cma_magic_number = "Caml1999A029"
     ; cmx_magic_number = "Caml1999y029"
     ; cmxa_magic_number = "Caml1999z029"
     ; ast_impl_magic_number = "Caml1999M029"
     ; ast_intf_magic_number = "Caml1999N029"
     ; cmxs_magic_number = "Caml1999D029"
     ; cmt_magic_number = "Caml1999T029"
     ; natdynlink_supported = true
     ; supports_shared_libraries = true
     ; windows_unicode = false
     }
 }
Actual targets:
- recursive alias @lib/default
- _build/default/rewriter.exe
- _build/default/rewriter_p5.exe
Running[1]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlc.opt -g -w -24 -I .ppx/bfcab61e6a21ecf6d2f80029fc1ef484 -I /media/work/.opam/4.12.1+flambda/lib/base -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types -I /media/work/.opam/4.12.1+flambda/lib/base/caml -I /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/common -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/shadow -I /media/work/.opam/4.12.1+flambda/lib/ocaml-migrate-parsetree -I /media/work/.opam/4.12.1+flambda/lib/ocaml/compiler-libs -I /media/work/.opam/4.12.1+flambda/lib/ppx_derivers -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/libname -I /media/work/.opam/4.12.1+flambda/lib/ppxlib -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/ast -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/print_diff -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/stdppx -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/traverse_builtins -I /media/work/.opam/4.12.1+flambda/lib/sexplib0 -I /media/work/.opam/4.12.1+flambda/lib/stdlib-shims -no-alias-deps -o .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/dune__exe___ppx.cmo -c -impl .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/_ppx.ml-gen)
Running[2]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlc.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -w -49 -nopervasives -nostdlib -g -bin-annot -I lib/.lib1.objs/byte -no-alias-deps -opaque -o lib/.lib1.objs/byte/lib1.cmo -c -impl lib/lib1.ml-gen)
Running[3]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -g -w -24 -I .ppx/bfcab61e6a21ecf6d2f80029fc1ef484 -I /media/work/.opam/4.12.1+flambda/lib/base -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types -I /media/work/.opam/4.12.1+flambda/lib/base/caml -I /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/common -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/shadow -I /media/work/.opam/4.12.1+flambda/lib/ocaml-migrate-parsetree -I /media/work/.opam/4.12.1+flambda/lib/ocaml/compiler-libs -I /media/work/.opam/4.12.1+flambda/lib/ppx_derivers -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/libname -I /media/work/.opam/4.12.1+flambda/lib/ppxlib -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/ast -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/print_diff -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/stdppx -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/traverse_builtins -I /media/work/.opam/4.12.1+flambda/lib/sexplib0 -I /media/work/.opam/4.12.1+flambda/lib/stdlib-shims -intf-suffix .ml-gen -no-alias-deps -o .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/dune__exe___ppx.cmx -c -impl .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/_ppx.ml-gen)
Running[4]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -w -49 -nopervasives -nostdlib -g -I lib/.lib1.objs/byte -I lib/.lib1.objs/native -intf-suffix .ml-gen -no-alias-deps -opaque -o lib/.lib1.objs/native/lib1.cmx -c -impl lib/lib1.ml-gen)
Running[5]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -g -w -24 -o .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/ppx.exe /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types/base_internalhash_types.cmxa -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types /media/work/.opam/4.12.1+flambda/lib/base/caml/caml.cmxa /media/work/.opam/4.12.1+flambda/lib/sexplib0/sexplib0.cmxa /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib/shadow_stdlib.cmxa /media/work/.opam/4.12.1+flambda/lib/base/base.cmxa -I /media/work/.opam/4.12.1+flambda/lib/base /media/work/.opam/4.12.1+flambda/lib/ocaml/compiler-libs/ocamlcommon.cmxa /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/common/ocaml_common.cmxa /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/shadow/ocaml_shadow.cmxa /media/work/.opam/4.12.1+flambda/lib/ocaml-migrate-parsetree/migrate_parsetree.cmxa /media/work/.opam/4.12.1+flambda/lib/stdlib-shims/stdlib_shims.cmxa /media/work/.opam/4.12.1+flambda/lib/ppxlib/ast/ppxlib_ast.cmxa /media/work/.opam/4.12.1+flambda/lib/ppxlib/print_diff/ppxlib_print_diff.cmxa /media/work/.opam/4.12.1+flambda/lib/ppx_derivers/ppx_derivers.cmxa /media/work/.opam/4.12.1+flambda/lib/ppxlib/traverse_builtins/ppxlib_traverse_builtins.cmxa /media/work/.opam/4.12.1+flambda/lib/ppxlib/stdppx/stdppx.cmxa /media/work/.opam/4.12.1+flambda/lib/ppxlib/ppxlib.cmxa /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/libname/ppx_inline_test_libname.cmxa /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/ppx_inline_test.cmxa .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/dune__exe___ppx.cmx)
Running[6]: (cd _build/default && .ppx/bfcab61e6a21ecf6d2f80029fc1ef484/ppx.exe --cookie 'inline_tests="enabled"' --cookie 'library-name="lib1"' -o lib/HelpersBase.pp.ml --impl lib/HelpersBase.ml -corrected-suffix .ppx-corrected -diff-cmd - -dump-ast)
Running[7]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamldep.opt -modules -impl lib/HelpersBase.pp.ml) > _build/default/lib/.lib1.objs/HelpersBase.pp.ml.d
Running[8]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlc.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -bin-annot -I lib/.lib1.objs/byte -I /media/work/.opam/4.12.1+flambda/lib/base -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types -I /media/work/.opam/4.12.1+flambda/lib/base/caml -I /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib -I /media/work/.opam/4.12.1+flambda/lib/jane-street-headers -I /media/work/.opam/4.12.1+flambda/lib/ppx_compare/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_enumerate/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_hash/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/config -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_sexp_conv/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/sexplib0 -I /media/work/.opam/4.12.1+flambda/lib/time_now -no-alias-deps -opaque -open Lib1 -o lib/.lib1.objs/byte/lib1__HelpersBase.cmo -c -impl lib/HelpersBase.pp.ml)
Running[9]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -I lib/.lib1.objs/byte -I lib/.lib1.objs/native -I /media/work/.opam/4.12.1+flambda/lib/base -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types -I /media/work/.opam/4.12.1+flambda/lib/base/caml -I /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib -I /media/work/.opam/4.12.1+flambda/lib/jane-street-headers -I /media/work/.opam/4.12.1+flambda/lib/ppx_compare/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_enumerate/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_hash/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/config -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_sexp_conv/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/sexplib0 -I /media/work/.opam/4.12.1+flambda/lib/time_now -intf-suffix .ml -no-alias-deps -opaque -open Lib1 -o lib/.lib1.objs/native/lib1__HelpersBase.cmx -c -impl lib/HelpersBase.pp.ml)
Running[10]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlc.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -a -o lib/lib1.cma lib/.lib1.objs/byte/lib1.cmo lib/.lib1.objs/byte/lib1__HelpersBase.cmo)
Running[11]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -a -o lib/lib1.cmxa lib/.lib1.objs/native/lib1.cmx lib/.lib1.objs/native/lib1__HelpersBase.cmx)
Running[12]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -shared -linkall -I lib -o lib/lib1.cmxs lib/lib1.cmxa)
Running[13]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlc.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -bin-annot -I .rewriter.eobjs/byte -I /media/work/.opam/4.12.1+flambda/lib/base -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types -I /media/work/.opam/4.12.1+flambda/lib/base/caml -I /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib -I /media/work/.opam/4.12.1+flambda/lib/camlp5 -I /media/work/.opam/4.12.1+flambda/lib/jane-street-headers -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/common -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/shadow -I /media/work/.opam/4.12.1+flambda/lib/ocaml-migrate-parsetree -I /media/work/.opam/4.12.1+flambda/lib/ocaml/compiler-libs -I /media/work/.opam/4.12.1+flambda/lib/ppx_compare/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_derivers -I /media/work/.opam/4.12.1+flambda/lib/ppx_enumerate/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_hash/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/config -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_sexp_conv/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppxlib -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/ast -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/print_diff -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/stdppx -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/traverse_builtins -I /media/work/.opam/4.12.1+flambda/lib/sexplib0 -I /media/work/.opam/4.12.1+flambda/lib/stdlib-shims -I /media/work/.opam/4.12.1+flambda/lib/time_now -I lib/.lib1.objs/byte -no-alias-deps -opaque -o .rewriter.eobjs/byte/dune__exe__Rewriter.cmo -c -impl rewriter.ml)
Running[14]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/mkcamlp5.opt -package camlp5,camlp5.pa_o,camlp5.pr_o,camlp5.extend,camlp5.quotations lib/lib1.cmxa -verbose -o rewriter_p5.exe)
Output[14]:
ocamlfind ocamlopt -predicates syntax,preprocessor,native -package camlp5,camlp5,camlp5.pa_o,camlp5.pr_o,camlp5.extend,camlp5.quotations -verbose -linkall -linkpkg lib/lib1.cmxa -o rewriter_p5.exe odyl.cmx
Effective set of compiler predicates: pkg_camlp5,pkg_camlp5.pa_o,pkg_camlp5.pr_o,pkg_camlp5.extend,pkg_camlp5.quotations,autolink,native,syntax,preprocessor,native
+ ocamlopt.opt -verbose -linkall -o rewriter_p5.exe -I /media/work/.opam/4.12.1+flambda/lib/camlp5 \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/odyl.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/camlp5.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/pa_o.cmx \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/pr_o.cmx \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/pr_op.cmx \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/pa_extend.cmx \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/q_MLast.cmx \
  lib/lib1.cmxa \
  odyl.cmx
File "_none_", line 1:
Error: No implementations provided for the following modules:
         Inline_test_config referenced from lib/lib1.cmxa(Lib1__HelpersBase)
         Ppx_inline_test_lib__Runtime referenced from lib/lib1.cmxa(Lib1__HelpersBase)
ocamlopt.opt returned with exit code 2
"ocamlfind" unexpectedly returned exit value 2 at /media/work/.opam/4.12.1+flambda/bin/mkcamlp5.opt line 108.
File "dune", line 13, characters 0-226:
13 | (rule
14 |  (targets rewriter_p5.exe)
15 |  (deps %{project_root}/lib/lib1.cmxa)
....22 |    -verbose
23 |    -o
24 |    %{targets})))
Error: Rule failed to generate the following targets:
- rewriter_p5.exe
Running[15]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g -I .rewriter.eobjs/byte -I .rewriter.eobjs/native -I /media/work/.opam/4.12.1+flambda/lib/base -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types -I /media/work/.opam/4.12.1+flambda/lib/base/caml -I /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib -I /media/work/.opam/4.12.1+flambda/lib/camlp5 -I /media/work/.opam/4.12.1+flambda/lib/jane-street-headers -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/common -I /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/shadow -I /media/work/.opam/4.12.1+flambda/lib/ocaml-migrate-parsetree -I /media/work/.opam/4.12.1+flambda/lib/ocaml/compiler-libs -I /media/work/.opam/4.12.1+flambda/lib/ppx_compare/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_derivers -I /media/work/.opam/4.12.1+flambda/lib/ppx_enumerate/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_hash/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/config -I /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppx_sexp_conv/runtime-lib -I /media/work/.opam/4.12.1+flambda/lib/ppxlib -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/ast -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/print_diff -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/stdppx -I /media/work/.opam/4.12.1+flambda/lib/ppxlib/traverse_builtins -I /media/work/.opam/4.12.1+flambda/lib/sexplib0 -I /media/work/.opam/4.12.1+flambda/lib/stdlib-shims -I /media/work/.opam/4.12.1+flambda/lib/time_now -I lib/.lib1.objs/byte -I lib/.lib1.objs/native -intf-suffix .ml -no-alias-deps -opaque -o .rewriter.eobjs/native/dune__exe__Rewriter.cmx -c -impl rewriter.ml)

Running[16]: (cd _build/default && /media/work/.opam/4.12.1+flambda/bin/ocamlopt.opt -w @1..3@5..28@30..39@43@46..47@49..57@61..62-40 -strict-sequence -strict-formats -short-paths -keep-locs -g \
  -o rewriter.exe \
  /media/work/.opam/4.12.1+flambda/lib/ocaml/compiler-libs/ocamlcommon.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/common/ocaml_common.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ocaml-compiler-libs/shadow/ocaml_shadow.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ocaml-migrate-parsetree/migrate_parsetree.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/stdlib-shims/stdlib_shims.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppxlib/ast/ppxlib_ast.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppxlib/print_diff/ppxlib_print_diff.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppx_derivers/ppx_derivers.cmxa /media/work/.opam/4.12.1+flambda/lib/ppxlib/traverse_builtins/ppxlib_traverse_builtins.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/sexplib0/sexplib0.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppxlib/stdppx/stdppx.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppxlib/ppxlib.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types/base_internalhash_types.cmxa \
  -I /media/work/.opam/4.12.1+flambda/lib/base/base_internalhash_types \
  /media/work/.opam/4.12.1+flambda/lib/base/caml/caml.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/base/shadow_stdlib/shadow_stdlib.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/base/base.cmxa \
  -I /media/work/.opam/4.12.1+flambda/lib/base \
  /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/config/inline_test_config.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/jane-street-headers/jane_street_headers.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppx_sexp_conv/runtime-lib/ppx_sexp_conv_lib.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppx_compare/runtime-lib/ppx_compare_lib.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppx_enumerate/runtime-lib/ppx_enumerate_lib.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/ppx_hash/runtime-lib/ppx_hash_lib.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/time_now/time_now.cmxa \
  -I /media/work/.opam/4.12.1+flambda/lib/time_now \
  /media/work/.opam/4.12.1+flambda/lib/ppx_inline_test/runtime-lib/ppx_inline_test_lib.cmxa \
  lib/lib1.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/odyl.cmxa \
  /media/work/.opam/4.12.1+flambda/lib/camlp5/camlp5.cmxa \
  .rewriter.eobjs/native/dune__exe__Rewriter.cmx)
````
