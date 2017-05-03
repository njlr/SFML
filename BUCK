include_defs('//BUCKAROO_DEPS')

cxx_library(
  name = 'sfml-graphics',
  header_namespace = '',
  srcs = glob(['src/SFML/Graphics/**/*.cpp']),
  headers = subdir_glob([
    ('src', 'SFML/Graphics/**/*.hpp')
  ]),
  exported_headers = subdir_glob([
    ('include', 'SFML/Graphics.hpp'),
    ('include', 'SFML/Graphics/**/*.inl'),
    ('include', 'SFML/Graphics/**/*.hpp')
  ]),
  deps = BUCKAROO_DEPS,
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  exported_linker_flags = ['-lGL'],
  visibility = ['PUBLIC']
)
