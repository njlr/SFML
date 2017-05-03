include_defs('//BUCKAROO_DEPS')

cxx_library(
  name = 'sfml-window',
  header_namespace = '',
  srcs = glob(['src/SFML/Window/*.cpp']),
  platform_srcs = [
    ('default', glob(['src/SFML/Window/Unix/**/*.cpp'])),
    ('^linux.*', glob(['src/SFML/Window/Unix/**/*.cpp'])),
    ('^macos.*', glob(['src/SFML/Window/OSX/**/*.cpp'])),
    ('^windows.*', glob(['src/SFML/Window/Win32/**/*.cpp'])),
    ('^bsd.*', glob(['src/SFML/Window/FreeBSD/**/*.cpp'])),
    ('^android.*', glob(['src/SFML/Window/Android/**/*.cpp']))
  ],
  headers = subdir_glob([
    ('src', 'SFML/Window/**/*.hpp')
  ]),
  exported_headers = subdir_glob([
    ('include', 'SFML/Window.hpp'),
    ('include', 'SFML/Window/**/*.inl'),
    ('include', 'SFML/Window/**/*.hpp')
  ]),
  deps = BUCKAROO_DEPS,
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  exported_platform_linker_flags = [
    ('default', ['-lX11', '-lGL', '-lXrandr', '-ludev']),
    ('^linux.*', ['-lX11', '-lGL', '-lXrandr', '-ludev'])
  ],
  visibility = ['PUBLIC']
)
