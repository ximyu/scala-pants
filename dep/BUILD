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

make_lib('commons-lang', 'commons-lang', '2.5')

make_lib('com.google.protobuf', 'protobuf-java', '2.4.1', 'protobuf-2.4.1')

make_lib('org.apache.thrift', 'libthrift', '0.5.0-1', 'libthrift-0.5.0')

scala_lib('jline', '2.10.3')
scala_lib('scala-library', '2.10.3')
scala_lib('scala-compiler', '2.10.3')
scala_lib('scala-reflect', '2.10.3')

SLF4J_VERSION = '1.6.1'
make_lib('org.slf4j', 'slf4j-api', SLF4J_VERSION)
make_lib('org.slf4j', 'slf4j-jdk14', SLF4J_VERSION)

jar_library(name = 'thrift-0.5.0',
  dependencies = [
    pants(':commons-lang'),
    pants(':libthrift-0.5.0'),
    pants(':slf4j-api'),
    pants(':slf4j-jdk14'),
  ]
)

#### Twitter-specific dependencies ####
FINAGLE_REV = '6.8.1'
UTIL_REV = '6.8.1'
SCROOGE_REV = '3.10.2'

def make_finagle(name):
  finagle_name = 'finagle-' + name
  return make_lib('com.twitter', finagle_name + '_2.10', FINAGLE_REV, finagle_name)

def make_util(name):
  util_name = 'util-' + name
  return make_lib('com.twitter', util_name + '_2.10', UTIL_REV, util_name)

def make_scrooge(name):
  scrooge_name = 'scrooge-' + name
  return make_lib('com.twitter', scrooge_name + '_2.10', SCROOGE_REV, scrooge_name)

make_finagle('core')
make_finagle('thrift')

make_util('core')

make_scrooge('core')
