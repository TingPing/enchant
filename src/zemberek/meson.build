shared_module('enchant_zemberek',
  'zemberek.cpp', 'zemberek_provider.cpp',
  dependencies: [
    dependency('dbus-glib-1', version: '>= 0.62'),
    enchant_internal_dep
  ],
  install: true,
  install_dir: enchant_libdir
)

message('The Zemberek is known to cause crashes with WebKit. Use at your own discretion.')
