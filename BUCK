include_defs('//BUCKAROO_DEPS')

windows_sources = glob([
  'src/SFML/Network/Win32/**/*.cpp',
])

unix_sources = glob([
  'src/SFML/Network/Unix/**/*.cpp',
])

platform_sources = windows_sources + unix_sources;

cxx_library(
  name = 'network',
  header_namespace = 'SFML',
  exported_headers = subdir_glob([
    ('include/SFML', 'Network.hpp'),
    ('include/SFML', 'Network/**/*.inl'),
    ('include/SFML', 'Network/**/*.hpp'),
  ]),
  headers = subdir_glob([
    ('src/SFML', 'Network/**/*.hpp'),
  ]),
  srcs = glob([
    'src/SFML/Network/**/*.cpp',
  ],
  excludes = platform_sources),
  platform_srcs = [
    ('^windows.*', windows_sources),
    ('.*', unix_sources),
  ],
  deps = BUCKAROO_DEPS,
  visibility = [
    'PUBLIC',
  ],
)
