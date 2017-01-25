# Sadly doesn't provide pc file
cc = meson.get_compiler('c')
voikko_lib = cc.find_library('voikko')

shared_module('enchant_voikko',
  'voikko_provider.c',
  dependencies: [
    voikko_lib,
    enchant_internal_dep
  ],
  install: true,
  install_dir: enchant_libdir
)
