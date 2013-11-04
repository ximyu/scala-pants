def make_lib(org, name, rev, alias=None):
  lib = jar_library(name=name,
    dependencies=[
      jar(org=org, name=name, rev=rev).with_sources()
    ]
  )
  if alias:
    jar_library(name=alias, dependencies=[lib])
  return lib

def scala_lib(name, rev):
  return make_lib('org.scala-lang', name, rev)

make_lib('com.google.protobuf', 'protobuf-java', '2.4.1', 'protobuf-2.4.1')

scala_lib('jline', '2.10.3')
scala_lib('scala-library', '2.10.3')
scala_lib('scala-compiler', '2.10.3')
scala_lib('scala-reflect', '2.10.3')
