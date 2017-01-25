myspell_dict_dir = join_paths(get_option('prefix'), get_option('datadir'), 'myspell/dicts')

shared_module('enchant_myspell',
  'myspell_checker.cpp',
  dependencies: [
    dependency('hunspell'),
    enchant_internal_dep
  ],
  c_args: [
    '-DENCHANT_MYSPELL_DICT_DIR="@0@"'.format(myspell_dict_dir)
  ],
  install: true,
  install_dir: enchant_libdir
)
