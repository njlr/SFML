include_defs('//BUCKAROO_DEPS')

linux_exported_linker_flags = [
  '-lX11',
  '-lGL',
  '-lpthread',
]

unix_sources = glob([
  'src/SFML/System/Unix/**/*.cpp',
])

windows_sources = glob([
  'src/SFML/System/Win32/**/*.cpp',
])

android_sources = glob([
  'src/SFML/System/Android/**/*.cpp',
])

cxx_library(
  name = 'system',
  header_namespace = 'SFML',
  exported_headers = subdir_glob([
    ('include/SFML', 'Config.hpp'),
    ('include/SFML', 'System.hpp'),
    ('include/SFML', 'System/**/*.hpp'),
    ('include/SFML', 'System/**/*.inl'),
  ]),
  headers = subdir_glob([
    ('src/SFML', 'System/**/*.hpp'),
  ]),
  srcs = glob([
    'src/SFML/System/*.cpp',
  ]),
  platform_srcs = [
    ('default', unix_sources),
    ('^linux.*', unix_sources),
    ('^macos.*', unix_sources),
    ('^windows.*', windows_sources),
    ('^android.*', android_sources),
  ],
  exported_preprocessor_flags = [
    '-DHAVE_PROTOTYPES=1',
  ],
  exported_platform_linker_flags = [
    ('default', linux_exported_linker_flags),
    ('^linux.*', linux_exported_linker_flags),
  ],
  visibility = [
    'PUBLIC',
  ],
)
