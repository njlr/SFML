include_defs('//BUCKAROO_DEPS')

prebuilt_cxx_library(
  name = 'sfml-openal',
  header_only = True,
  exported_headers = subdir_glob([
    ('extlibs/headers/AL', '*.h')
  ]),
  exported_linker_flags = ['-lopenal']
)

cxx_library(
  name = 'sfml-audio',
  header_namespace = '',
  srcs = glob(['src/SFML/Audio/**/*.cpp']),
  headers = subdir_glob([
    ('src', 'SFML/Audio/**/*.hpp')
  ]),
  exported_headers = subdir_glob([
    ('include', 'SFML/Audio.hpp'),
    ('include', 'SFML/Audio/**/*.inl'),
    ('include', 'SFML/Audio/**/*.hpp')
  ]),
  deps = [':sfml-openal'] + BUCKAROO_DEPS,
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  visibility = ['PUBLIC']
)
