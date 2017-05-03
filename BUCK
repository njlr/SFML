include_defs('//BUCKAROO_DEPS')

windows_network_srcs = glob(['src/SFML/Network/Win32/**/*.cpp']);
unix_network_srcs = glob(['src/SFML/Network/Unix/**/*.cpp']);
network_platform_srcs = windows_network_srcs + unix_network_srcs;

cxx_library(
  name = 'sfml-network',
  header_namespace = '',
  srcs = glob(
    ['src/SFML/Network/**/*.cpp'],
    excludes = network_platform_srcs
  ),
  platform_srcs = [
    ('^windows.*', windows_network_srcs),
    ('.*', unix_network_srcs)
  ],
  headers = subdir_glob([
    ('src', 'SFML/Network/**/*.hpp')
  ]),
  exported_headers = subdir_glob([
    ('include', 'SFML/Network.hpp'),
    ('include', 'SFML/Network/**/*.inl'),
    ('include', 'SFML/Network/**/*.hpp')
  ]),
  deps = BUCKAROO_DEPS,
  exported_preprocessor_flags = ['-DSFML_DEPRECATED='],
  visibility = ['PUBLIC']
)
