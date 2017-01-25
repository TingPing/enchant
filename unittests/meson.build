unittest_env = [
  'ENCHANT_MODULE_PATH=@0@/mock_provider'.format(meson.current_build_dir())
]

libunittestpp_dep = dependency('unittest++')

unittest_deps = [
  enchant_external_dep,
  libunittestpp_dep,
]

unittest_cxxflags = []

if not cxx.has_header('UnitTest++', dependencies: libunittestpp_dep)
  # The pkgconfig file has the wrong includedir..?
  incdir = libunittestpp_dep.get_pkgconfig_variable('includedir')
  unittest_cxxflags += '-I' + join_paths(incdir, 'UnitTest++')
endif

unittest_source = [
  'main.cpp',
  'dictionary/enchant_dict_add_tests.cpp',
  'dictionary/enchant_dict_add_to_session_tests.cpp',
  'dictionary/enchant_dict_check_tests.cpp',
  'dictionary/enchant_dict_describe_tests.cpp',
  'dictionary/enchant_dict_free_string_list_tests.cpp',
  'dictionary/enchant_dict_get_error_tests.cpp',
  'dictionary/enchant_dict_is_added_tests.cpp',
  'dictionary/enchant_dict_is_removed_tests.cpp',
  'dictionary/enchant_dict_remove_from_session_tests.cpp',
  'dictionary/enchant_dict_remove_tests.cpp',
  'dictionary/enchant_dict_store_replacement_tests.cpp',
  'dictionary/enchant_dict_suggest_tests.cpp',
  'broker/enchant_broker_describe_tests.cpp',
  'broker/enchant_broker_dict_exists_tests.cpp',
  'broker/enchant_broker_free_dict_tests.cpp',
  'broker/enchant_broker_free_tests.cpp',
  'broker/enchant_broker_get_error_tests.cpp',
  'broker/enchant_broker_init_tests.cpp',
  'broker/enchant_broker_list_dicts_tests.cpp',
  'broker/enchant_broker_request_dict_tests.cpp',
  'broker/enchant_broker_request_pwl_dict_tests.cpp',
  'broker/enchant_broker_set_ordering_tests.cpp',
  'pwl/enchant_pwl_tests.cpp',
  'provider/enchant_provider_broker_set_error_tests.cpp',
  'provider/enchant_provider_dict_set_error_tests.cpp',
  'provider/enchant_provider_get_prefix_dir_tests.cpp',
  'provider/enchant_provider_get_user_config_dirs_tests.cpp',
  'provider/enchant_provider_get_user_language_tests.cpp',
]

subdir('mock_provider')
subdir('enchant_providers') # FIXME: Should depend upon mock_providers

unittests = executable('unittests',
  unittest_source,
  cpp_args: unittest_cxxflags,
  dependencies: unittest_deps,
)
# test('unittests', unittests, env: unittest_env)

# These unittests are largely broken and they don't fit
# into the normal test support as it handles its own
# summaries and failures. So just make it `ninja unittest`
run_target('unittest',
  command: ['env', unittest_env[0], unittests],
  depends: mock_providers,
  # FIXME: Meson doesn't support passing env yet
)

