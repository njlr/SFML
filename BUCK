include_defs('//BUCKAROO_DEPS')

linux_exported_linker_flags = [
  '-lGL',
]

cxx_library(
  name = 'graphics',
  header_namespace = 'SFML',
  exported_headers = subdir_glob([
    ('include/SFML', 'Graphics.hpp'),
    ('include/SFML', 'Graphics/**/*.inl'),
    ('include/SFML', 'Graphics/**/*.hpp'),
  ]),
  headers = subdir_glob([
    ('src/SFML', 'Graphics/**/*.hpp'),
  ]),
  srcs = glob([
    'src/SFML/Graphics/**/*.cpp',
  ]),
  exported_preprocessor_flags = [
    '-DHAVE_PROTOTYPES=1',
  ],
  exported_platform_linker_flags = [
    ('linux', linux_exported_linker_flags),
  ],
  deps = BUCKAROO_DEPS,
  visibility = [
    'PUBLIC'
  ],
)
