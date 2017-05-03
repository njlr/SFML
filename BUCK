include_defs('//BUCKAROO_DEPS')

macos_exported_linker_flags = [
  '-framework', 'openal',
]

linux_exported_linker_flags = [
  '-lopenal',
]

prebuilt_cxx_library(
  name = 'openal',
  header_only = True,
  header_namespace = '',
  exported_headers = subdir_glob([
    ('extlibs/headers/AL', '**/*.h'),
  ]),
  exported_platform_linker_flags = [
    ('default', macos_exported_linker_flags),
    ('^linux.*', linux_exported_linker_flags),
    ('^macos.*', macos_exported_linker_flags),
  ],
)

cxx_library(
  name = 'audio',
  header_namespace = 'SFML',
  exported_headers = subdir_glob([
    ('include/SFML', 'Audio.hpp'),
    ('include/SFML', 'Audio/**/*.inl'),
    ('include/SFML', 'Audio/**/*.hpp'),
  ]),
  headers = subdir_glob([
    ('src/SFML', 'Audio/**/*.hpp'),
  ]),
  srcs = glob([
    'src/SFML/Audio/**/*.cpp',
  ]),
  exported_preprocessor_flags = [
    '-DHAVE_PROTOTYPES=1',
  ],
  deps = BUCKAROO_DEPS + [
    ':openal',
  ],
  visibility = [
    'PUBLIC',
  ],
)
