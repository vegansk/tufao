find_package(PkgConfig)

# Build info
configure_file(tufao.prf.in tufao${TUFAO_VERSION_MAJOR}.prf @ONLY)
if(PKG_CONFIG_FOUND)
    configure_file(tufao.pc.in tufao${TUFAO_VERSION_MAJOR}.pc @ONLY)
endif(PKG_CONFIG_FOUND)
configure_file(FindTufao.cmake.in FindTufao${TUFAO_VERSION_MAJOR}.cmake @ONLY)

# Install info
if(TUFAO_MKSPECS_MODULE_DIR)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/tufao${TUFAO_VERSION_MAJOR}.prf"
        DESTINATION "${TUFAO_MKSPECS_MODULE_DIR}"
        COMPONENT development
    )
else(TUFAO_MKSPECS_MODULE_DIR)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/tufao${TUFAO_VERSION_MAJOR}.prf"
        DESTINATION "${QT_MKSPECS_DIR}/features"
        COMPONENT development
    )
endif(TUFAO_MKSPECS_MODULE_DIR)

if(PKG_CONFIG_FOUND)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/tufao${TUFAO_VERSION_MAJOR}.pc"
            DESTINATION "${libdir}/pkgconfig"
            COMPONENT development
    )
endif(PKG_CONFIG_FOUND)
if(TUFAO_CMAKE_MODULE_DIR)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/FindTufao${TUFAO_VERSION_MAJOR}.cmake"
        DESTINATION "${TUFAO_CMAKE_MODULE_DIR}"
        COMPONENT development
    )
else(TUFAO_CMAKE_MODULE_DIR)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/FindTufao${TUFAO_VERSION_MAJOR}.cmake"
        DESTINATION "${CMAKE_ROOT}/Modules"
        COMPONENT development
    )
endif(TUFAO_CMAKE_MODULE_DIR)
