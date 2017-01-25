# TODO: -DENCHANT_ISPELL_DICT_DIR

ispell_sources = [
  'correct.cpp',
  'good.cpp',
  'hash.cpp',
  'ispell_checker.cpp',
  'lookup.cpp',
  'makedent.cpp',
  'tgood.cpp'
]

shared_module('enchant_ispell',
  ispell_sources,
  dependencies: [
    enchant_internal_dep
  ],
  install: true,
  install_dir: enchant_libdir
)
