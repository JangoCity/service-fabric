set( LINUX_SOURCES
    ../Constants.cpp
    ../CentralSecretServiceConfig.cpp
    ../ClientRequestAsyncOperation.cpp
    ../GetSecretsAsyncOperation.cpp
    ../SetSecretsAsyncOperation.cpp
    ../RemoveSecretsAsyncOperation.cpp
    ../CentralSecretServiceReplica.cpp
    ../CentralSecretServiceFactory.cpp
    ../SecretDataItem.cpp
    ../Crypto.cpp
    ../SecretManager.cpp
)

include_directories("..")

add_library(objects_CentralSecretService OBJECT ${LINUX_SOURCES})

add_precompiled_header(objects_CentralSecretService ../stdafx.h)

add_library(${lib_CentralSecretService} STATIC $<TARGET_OBJECTS:objects_CentralSecretService>)

set_target_properties(${lib_CentralSecretService} PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY ${LIBRARY_OUTPUT_DIR})

target_link_libraries(${lib_CentralSecretService}
  ${lib_ResourceManager}
)
