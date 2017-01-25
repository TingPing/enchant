test_env = [
  # TODO
  'ENCHANT_MODULE_PATH=' + '@0@/src/applespell:@0@/src/myspell'.format(meson.build_root())
]

bin_cflags = [
  '-DPACKAGE_VERSION="@0@"'.format(meson.project_version())
]

executable('enchant',
  'enchant-ispell.c',
  c_args: bin_cflags,
  dependencies: enchant_external_dep,
  install: true
)

executable('enchant-lsmod',
  'enchant-lsmod.c',
  c_args: bin_cflags,
  dependencies: enchant_external_dep,
  install: true
)

enchant_test = executable('enchant-test',
  'enchant.test.c',
  dependencies: enchant_external_dep
)
test('enchant-test', enchant_test, env: test_env)

enchantxx_test = executable('enchantxx-test',
  'enchantxx.test.cpp',
  dependencies: enchant_external_dep
)
test('enchantxx-test', enchantxx_test, env: test_env)
