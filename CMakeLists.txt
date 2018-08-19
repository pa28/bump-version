
configure_file(current_version.in current_version @ONLY)
configure_file(bump_version.in bump_version @ONLY)

add_custom_target(bump_tweak COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l tweak -t -p)

add_custom_target(bump_patch COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l patch -t -p)

add_custom_target(bump_minor COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l minor -t -p)

add_custom_target(bump_major COMMAND ${CMAKE_CURRENT_BINARY_DIR}/bump_version -l major -t -p)
