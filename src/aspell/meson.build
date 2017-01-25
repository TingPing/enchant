# Sadly doesn't provide pc file
cc = meson.get_compiler('c')
aspell_lib = cc.find_library('aspell')
aspell_cflags = []

if cc.has_header('pspell/pspell.h')
  aspell_cflags += '-DASPELL_0_50_0=1'
  aspell_cflags += '-DHAVE_PSPELL_H'
elif cc.has_header('aspell.h')
  aspell_cflags += '-DASPELL_0_50_0=1'
else
  error('Failed to find aspell.h or pspell.h')
endif

shared_module('enchant_aspell',
  'aspell_provider.c',
  dependencies: [
    aspell_lib,
    enchant_internal_dep
  ],
  c_args: aspell_cflags,
  install: true,
  install_dir: enchant_libdir
)
