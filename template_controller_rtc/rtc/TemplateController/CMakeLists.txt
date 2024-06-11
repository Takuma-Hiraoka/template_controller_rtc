add_definitions(-Wno-deprecated)

find_package(catkin REQUIRED COMPONENTS
  rtmbuild2
  template_controller_msgs
  )
include_directories(
  ${catkin_INCLUDE_DIRS}
  ${openrtm_aist_INCLUDE_DIRS}
  )

add_library(TemplateController SHARED
  TemplateController.cpp
  TemplateControllerService_impl.cpp
  )
target_link_libraries(TemplateController
  ${catkin_LIBRARIES}
  ${openrtm_aist_LIBRARIES}
  ${${PROJECT_NAME}_IDLLIBRARY_DIRS}
  )
set_target_properties(TemplateController PROPERTIES PREFIX "") # libTemplateController.so -> TemplateController.so
add_dependencies(TemplateController RTMBUILD2_${PROJECT_NAME}_genrpc) # wait for rtmbuild2_genidl

add_executable(TemplateControllerComp TemplateControllerComp.cpp)
target_link_libraries(TemplateControllerComp TemplateController)
