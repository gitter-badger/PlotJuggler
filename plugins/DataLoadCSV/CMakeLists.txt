
include_directories( ./ ../  ../../include  ../../common)

add_definitions(${QT_DEFINITIONS})
add_definitions(-DQT_PLUGIN)
add_definitions(-DQT_SHARED)

QT5_WRAP_UI ( UI_SRC  ../../common/selectlistdialog.ui  )

SET( SRC
    dataload_csv.cpp
    ../../common/selectlistdialog.h
    )

add_library(DataLoadCSV SHARED ${SRC} ${UI_SRC}  )
target_link_libraries(DataLoadCSV  ${Qt5Widgets_LIBRARIES} )


if(catkin_FOUND)
    install(TARGETS DataLoadCSV
        ARCHIVE DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
        LIBRARY DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
        RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION} )
elseif()
    install(TARGETS DataLoadCSV DESTINATION bin  )
endif()
