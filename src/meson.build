enchant_sources = [
  'enchant.c',
  'pwl.c',
]

enchant_deps = [
  dependency('glib-2.0'),
  dependency('gmodule-2.0')
]

enchant_public_headers = [
  'enchant.h',
  'enchant-provider.h',
  'enchant++.h'
]

install_headers(enchant_public_headers, subdir: 'enchant')

enchant_libdir = join_paths(get_option('prefix'), get_option('libdir'), 'enchant')

enchant_cflags = [
  '-D_ENCHANT_BUILD=1',
  '-DENCHANT_GLOBAL_MODULE_DIR="@0@"'.format(enchant_libdir),
  '-DENCHANT_GLOBAL_ORDERING="@0@"'.format(enchant_ordering_dir),
  '-DENCHANT_VERSION_STRING="@0@"'.format(meson.project_version())
]

cc = meson.get_compiler('c')

if target_machine.system() == 'windows'
  split_version = meson.project_version().split('.')

  rc_conf = configuration_data()
  rc_conf.set('ENCHANT_MAJOR_VERSION', split_version[0])
  rc_conf.set('ENCHANT_MINOR_VERSION', split_version[1])
  rc_conf.set('ENCHANT_MICRO_VERSION', split_version[2])

  rc_file = configure_file(
    input: 'libenchant.rc.in',
    output: 'libenchant.rc',
    configuration: rc_conf
  )

  windows = import('windows')
  enchant_sources += window.compile_resources(rc_file)

  if cc.get_id() == 'msvc'
    enchant_cflags += '-FI@0@/config.h.win32'.format(meson.current_source_dir())
  endif
endif

# Used in pwl.c
if cc.has_function('flock')
  enchant_cflags += '-DHAVE_FLOCK=1'
endif
if cc.has_function('lockf')
  enchant_cflags += '-DHAVE_LOCKF=1'
endif

if cc.has_header_symbol('locale.h', 'LC_MESSAGES')
  enchant_cflags += '-DHAVE_LC_MESSAGES=1'
endif


enchant_lib = library('enchant',
  enchant_sources,
  dependencies: enchant_deps,
  c_args: enchant_cflags,
  # FIXME: Matches Autotools version which was wrong
  version: meson.project_version(),
  # TODO: map file
  install: true
)

# This is used for our plugins
enchant_internal_dep = declare_dependency(
  include_directories: include_directories('.'),
  dependencies: enchant_deps,
  c_args: '-D_ENCHANT_BUILD=1'
)

enchant_external_dep = declare_dependency(
  include_directories: include_directories('.'),
  link_with: enchant_lib,
  dependencies: enchant_deps,
)

modules = [
  'myspell', 'aspell', 'hspell', 'uspell',
  'voikko', 'zemberek', 'ispell'
]

foreach module: modules
  if get_option('with-' + module)
    subdir(module)
  endif
endforeach
