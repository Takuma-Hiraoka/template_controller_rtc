cmake_minimum_required(VERSION 3.0.2)
project(template_controller_msgs)

# add_compile_options(-std=c++11)
# set(CMAKE_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS
  rtmbuild2
)

################################################
## Declare ROS messages, services and actions ##
################################################

## Generate messages in the 'msg' folder
# add_message_files(
#   FILES
#   Message1.msg
#   Message2.msg
# )

## Generate services in the 'srv' folder
# add_service_files(
#   FILES
#   Service1.srv
#   Service2.srv
# )

rtmbuild2_init() # ここにidlとmsgが依存する外部パッケージを書く

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if your package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#  INCLUDE_DIRS include
   LIBRARIES TemplateControllerSkel TemplateControllerStub
#   DEPENDS openrtm_aist
)

###########
## Build ##
###########

rtmbuild2_genidl()

add_custom_target(genidl All DEPENDS RTMBUILD2_${PROJECT_NAME}_genrpc)
