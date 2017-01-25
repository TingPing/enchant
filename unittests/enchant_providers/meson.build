providers_sources = [
  'main.cpp',
  'Dictionary/dictionary_check.cpp',
  'Dictionary/dictionary_suggest.cpp',
  'Provider/provider_describe_dict.cpp',
  'Provider/provider_dictionary_exists.cpp',
  'Provider/provider_identify_dict.cpp',
  'Provider/provider_list_dicts.cpp',
  'Provider/provider_request_dict.cpp',
]

providers_test = executable('providers-test',
  providers_sources,
  cpp_args: unittest_cxxflags,
  dependencies: unittest_deps,
)
test('providers-test', providers_test, env: unittest_env)
