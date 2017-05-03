include_defs('//BUCKAROO_DEPS')

cxx_library(
  name = 'sfml-system',
  header_namespace = '',
  srcs = glob(['src/SFML/System/*.cpp']),
  platform_srcs = [
    ('default', glob(['src/SFML/System/Unix/**/*.cpp'])),
    ('^linux.*', glob(['src/SFML/System/Unix/**/*.cpp'])),
    ('^macos.*', glob(['src/SFML/System/Unix/**/*.cpp'])),
    ('^windows.*', glob(['src/SFML/System/Win32/**/*.cpp'])),
    ('^android.*', glob(['src/SFML/System/Android/**/*.cpp']))
  ],
  headers = subdir_glob([
    ('src', 'SFML/System/**/*.hpp')
  ]),
  exported_headers = subdir_glob([
    ('include', 'SFML/System.hpp'),
    ('include', 'SFML/System/**/*.inl'),
    ('include', 'SFML/System/**/*.hpp')
  ]),
  deps = [],
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  exported_linker_flags = ['-lX11', '-lGL', '-lpthread'],
  visibility = ['PUBLIC']
)
