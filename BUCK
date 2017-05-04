include_defs('//BUCKAROO_DEPS')

unix_sources = glob([
  'src/SFML/Window/Unix/**/*.cpp',
])

macos_sources = glob([
  'src/SFML/Window/OSX/**/*.cpp',
  'src/SFML/Window/OSX/**/*.mm',
  'src/SFML/Window/OSX/**/*.m',
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

egl_sources = glob([
  'src/SFML/Window/EGL*.cpp',
  'src/SFML/Window/Egl*.cpp',
])

platform_sources = unix_sources + macos_sources + windows_sources + bsd_sources + android_sources + egl_sources

linux_exported_linker_flags = [
  '-lX11',
  '-lGL',
  '-lXrandr',
  '-ludev',
]

macos_exported_linker_flags = [
  '-framework', 'ApplicationServices',
  '-framework', 'CoreFoundation',
  '-framework', 'CoreServices',
  '-framework', 'IOKit',
  '-framework', 'OpenGL',
  '-framework', 'Cocoa',
  '-framework', 'Carbon',
]

cxx_library(
  name = 'window',
  header_namespace = 'SFML',
  exported_headers = subdir_glob([
    ('include/SFML', 'OpenGL.hpp'),
    ('include/SFML', 'Window.hpp'),
    ('include/SFML', 'Window/**/*.hpp'),
    ('include/SFML', 'Window/**/*.h'),
    ('include/SFML', 'Window/**/*.inl'),
  ]),
  headers = subdir_glob([
    ('src/SFML', 'Window/**/*.hpp'),
    ('src/SFML', 'Window/**/*.h'),
    ('src/SFML', 'Window/**/*.inl'),
  ]),
  srcs = glob([
    'src/SFML/Window/*.cpp',
  ], excludes = platform_sources),
  platform_srcs = [
    ('default', unix_sources),
    ('^linux.*', unix_sources),
    ('^macos.*', macos_sources),
    ('^windows.*', windows_sources),
    ('^bsd.*', bsd_sources),
    ('^android.*', android_sources + egl_sources),
  ],
  exported_platform_linker_flags = [
    ('default', []),
    ('^linux.*', linux_exported_linker_flags),
    ('^macos.*', macos_exported_linker_flags),
  ],
  deps = BUCKAROO_DEPS,
  visibility = [
    'PUBLIC'
  ],
)
