# EGCL compatibility

The base mgl-pax system and bootstrap use portable Common Lisp on EGCL. Existing
SBCL-specific compiler-note suppression and policy bindings stay SBCL-only.

With this checkout and dependencies in ASDF's source registry, run:

```sh
egcl --no-init --load egcl-smoke.lisp
```

The smoke loads the base system, defines a documentation section, and checks
its class and title. It passed with EGCL 0.0.10 (b94618ece), under Evergreen's
2G memory cap. Use atgreen/named-readtables' EGCL iterator to avoid the portable
iterator's Unicode-wide scan.

This branch starts from f7f9414, the version in the audited ocicl installation.
The upstream location is https://github.com/melisgl/mgl-pax. A newer revision
advertised by ocicl (ccc3f6c) requires the new autoload dependency, absent from
that installation; updating to that dependency layout is not part of this port.

Full rendering, transcription, source navigation, SWANK integration, and the
upstream comprehensive test suite have not been validated. Core-section support
does not imply support for every implementation introspection feature.
