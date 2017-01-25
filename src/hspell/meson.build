# Sadly doesn't provide pc file
cc = meson.get_compiler('c')
hspell_lib = cc.find_library('hspell')

shared_module('enchant_hspell',
  'hspell_provider.c',
  dependencies: [
    hspell_lib,
    enchant_internal_dep
  ],
  install: true,
  install_dir: enchant_libdir
)
