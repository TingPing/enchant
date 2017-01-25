mock_providers = [
  shared_module('enchant_mock_provider',
    'mock_provider.cpp',
    dependencies: enchant_internal_dep
  ),

  shared_module('enchant_mock_provider2',
    'mock_provider.cpp',
    dependencies: enchant_internal_dep
  ),

  shared_module('enchant_null_provider',
    'mock_provider.cpp',
    cpp_args: '-DENCHANT_TEST_NULL_PROVIDER',
    dependencies: enchant_internal_dep
  ),

  shared_module('enchant_null_identify',
    'mock_provider.cpp',
    cpp_args: '-DENCHANT_TEST_NULL_IDENTIFY',
    dependencies: enchant_internal_dep
  ),

  shared_module('enchant_null_describe',
    'mock_provider.cpp',
    cpp_args: '-DENCHANT_TEST_NULL_DESCRIBE',
    dependencies: enchant_internal_dep
  )
]
