# Configure ShaderSystemTexturedFog demo build

set(HEADER_FILES 
	include/ShaderSystemTexturedFog.h
	include/RTShaderSRSTexturedFog.h
	)

set(SOURCE_FILES 
	src/ShaderSystemTexturedFog.cpp
	src/RTShaderSRSTexturedFog.cpp
  	)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
ogre_add_component_include_dir(RTShaderSystem)

ogre_add_library_to_folder(Samples Sample_ShaderSystemTexturedFog ${OGRE_LIB_TYPE} ${SOURCE_FILES} ${HEADER_FILES})

target_link_libraries(Sample_ShaderSystemTexturedFog ${OGRE_LIBRARIES} ${SDL2_LIBRARY})
ogre_config_sample_lib(Sample_ShaderSystemTexturedFog)

if (APPLE AND NOT APPLE_IOS)
    # Set the INSTALL_PATH so that Samples can be installed in the application package
    set_target_properties(Sample_ShaderSystemTexturedFog
       PROPERTIES BUILD_WITH_INSTALL_RPATH 1
       INSTALL_NAME_DIR "@executable_path/../Plugins"
    )
endif()



