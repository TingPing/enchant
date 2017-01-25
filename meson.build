project('enchant', ['c', 'cpp'],
  version: '1.6.1',
  meson_version: '>= 0.37.0',
  default_options: [
    'warning_level=2',
    'cpp_std=c++11',
  ]
)


cc = meson.get_compiler('c')
test_c_warn_flags = [
  '-Wsign-compare', '-Werror-implicit-function-declaration',
  '-Wpointer-arith', '-Wwrite-strings', '-Wstrict-prototypes',
  '-Wmissing-prototypes', '-Wmissing-declarations', '-Wnested-externs',
  '-Wpacked', '-Wswitch-enum', '-Wmissing-format-attribute',
  '-Wstrict-aliasing=2', '-Winit-self', '-Wunsafe-loop-optimizations',
  '-Wdeclaration-after-statement', '-Wold-style-definition',
  '-Wno-missing-field-initializers', '-Wno-unused-parameter',
  '-Wno-attributes', '-Wno-long-long', '-Winline', '-fno-strict-aliasing'
]
warn_c_flags = []
foreach flag: test_c_warn_flags
  if cc.has_argument(flag)
    warn_c_flags += flag
  endif
endforeach
add_project_arguments(warn_c_flags, language: 'c')

cxx = meson.get_compiler('cpp')
test_cxx_warn_flags = [
  '-Wsign-compare',
  '-Wpointer-arith', '-Wwrite-strings',
  '-Wpacked', '-Wswitch-enum', '-Wmissing-format-attribute',
  '-Wstrict-aliasing=2', '-Winit-self', '-Wunsafe-loop-optimizations',
  '-Wno-missing-field-initializers', '-Wno-unused-parameter',
  '-Wno-attributes', '-Wno-long-long', '-Winline', '-fno-strict-aliasing'
]
warn_cxx_flags = []
foreach flag: test_cxx_warn_flags
  if cxx.has_argument(flag)
    warn_cxx_flags += flag
  endif
endforeach
add_project_arguments(warn_cxx_flags, language: 'cpp')


pc_conf = configuration_data()
pc_conf.set('prefix', get_option('prefix'))
pc_conf.set('exec_prefix', '${prefix}')
pc_conf.set('libdir', join_paths('${exec_prefix}', get_option('libdir')))
pc_conf.set('includedir', join_paths('${prefix}', get_option('includedir')))
pc_conf.set('VERSION', meson.project_version())

configure_file(
  input: 'enchant.pc.in',
  output: 'enchant.pc',
  configuration: pc_conf,
  install: true,
  install_dir: join_paths(get_option('libdir'), 'pkgconfig')
)

enchant_ordering_dir = join_paths(get_option('prefix'), get_option('datadir'), 'enchant')
install_data('data/enchant.ordering', install_dir: enchant_ordering_dir)

install_man('doc/enchant.1')

subdir('src')
subdir('tests')
subdir('unittests')
