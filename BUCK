include_defs('//BUCKAROO_DEPS')

unix_sources = glob([
  'src/SFML/Window/Unix/**/*.cpp',
])

macos_sources = glob([
  'src/SFML/Window/OSX/**/*.cpp',
])

windows_sources = glob([
  'src/SFML/Window/Win32/**/*.cpp',
])

bsd_sources = glob([
  'src/SFML/Window/FreeBSD/**/*.cpp',
])

android_sources = glob([
  'src/SFML/Window/Android/**/*.cpp',
])

cxx_library(
  name = 'window',
  header_namespace = 'SFML',
  exported_headers = subdir_glob([
    ('include/SFML', 'Window.hpp'),
    ('include/SFML', 'Window/**/*.inl'),
    ('include/SFML', 'Window/**/*.hpp'),
  ]),
  headers = subdir_glob([
    ('src/SFML', 'Window/**/*.hpp'),
  ]),
  srcs = glob([
    'src/SFML/Window/*.cpp',
  ]),
  platform_srcs = [
    ('default', unix_sources),
    ('^linux.*', unix_sources),
    ('^macos.*', macos_sources),
    ('^windows.*', windows_sources),
    ('^bsd.*', bsd_sources),
    ('^android.*', android_sources),
  ],
  exported_preprocessor_flags = [
    '-DHAVE_PROTOTYPES=1',
  ],
  exported_platform_linker_flags = [
    ('default', ['-lX11', '-lGL', '-lXrandr', '-ludev']),
    ('^linux.*', ['-lX11', '-lGL', '-lXrandr', '-ludev']),
  ],
  deps = BUCKAROO_DEPS,
  visibility = [
    'PUBLIC'
  ],
)
