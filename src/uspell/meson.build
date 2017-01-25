# TODO: -DENCHANT_USPELL_DICT_DIR

shared_module('enchant_uspell',
  'uspell_provider.cpp',
  dependencies: [
    dependency('libuspell', version: '>= 1.1.0'),
    enchant_internal_dep
  ],
  install: true,
  install_dir: enchant_libdir
)
