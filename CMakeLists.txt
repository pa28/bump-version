
configure_file(current_version.in ${CMAKE_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/current_version @ONLY)
configure_file(bump_version.in ${CMAKE_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/bump_version @ONLY)

file(COPY {CMAKE_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/current_version
    DESTINATION ${CMAKE_BINARY_DIR}
    FILE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ)

file(COPY {CMAKE_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/bump_version
    DESTINATION ${CMAKE_BINARY_DIR}
    FILE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ)
    
add_custom_target(bump_tweak COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l tweak -t)

add_custom_target(bump_patch COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l patch -t)

add_custom_target(bump_minor COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l minor -t)

add_custom_target(bump_major COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l major -t)
