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
  deps = [':sfml-system'],
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  exported_platform_linker_flags = [
    ('default', ['-lX11', '-lGL', '-lXrandr', '-ludev']),
    ('^linux.*', ['-lX11', '-lGL', '-lXrandr', '-ludev'])
  ],
  visibility = ['PUBLIC']
)

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
  deps = [':sfml-window'] + BUCKAROO_DEPS, #stb_image #freetype2
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  exported_linker_flags = ['-lGL'],
  visibility = ['PUBLIC']
)

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
  deps = [':sfml-openal'],
  exported_preprocessor_flags = ['-DSFML_DEPRECATED=', '-DHAVE_PROTOTYPES=1'],
  visibility = ['PUBLIC']
)


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
  deps = [':sfml-system'],
  exported_preprocessor_flags = ['-DSFML_DEPRECATED='],
  visibility = ['PUBLIC']
)

prebuilt_cxx_library(
  name = 'sfml',
  header_namespace = 'SFML',
  header_only = True,
  exported_headers = subdir_glob([
    ('include/SFML', '**/*.hpp'),
    ('include/SFML', '**/*.inl')
  ]),
  deps = [':sfml-system', ':sfml-window', ':sfml-graphics', ':sfml-network', ':sfml-audio'],
  visibility = ['PUBLIC']
)
