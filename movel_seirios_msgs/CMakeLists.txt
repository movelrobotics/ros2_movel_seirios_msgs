cmake_minimum_required(VERSION 3.5)
project(movel_seirios_msgs)
set(CMAKE_CXX_STANDARD 14)

include(${PROJECT_SOURCE_DIR}/cmake/colorize.cmake)
include(${PROJECT_SOURCE_DIR}/cmake/cxxStandard.cmake)
set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(rosidl_default_runtime REQUIRED)

find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(diagnostic_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  # Msg
  "msg/CircleObstacle.msg"
  "msg/Cluster.msg"
  "msg/ClusterArray.msg"
  "msg/CustomTeleop.msg"
  "msg/DateTime.msg"
  "msg/DiagnosticState.msg"
  "msg/DiagnosticStateArray.msg"
  "msg/HardwareState.msg"
  "msg/LaserScanWithTF.msg"
  # "msg/movelPointcloud2.msg" # is an invalid message name.  It should have the pattern '^[A-Z][A-Za-z0-9]*$'
  "msg/Obstacles.msg"
  "msg/ObstructionStatus.msg"
  "msg/Pixel.msg"
  "msg/Point.msg"
  "msg/PointArray.msg"
  "msg/Polygon.msg"
  "msg/Reports.msg"
  "msg/SegmentObstacle.msg"
  "msg/SpeedZone.msg"
  "msg/States.msg"
  "msg/StringArray.msg"
  "msg/SubtaskFeedback.msg"
  "msg/Task.msg"
  "msg/TaskDuration.msg"
  "msg/TaskFeedback.msg"
  "msg/TaskHandlerFeedback.msg"
  "msg/TaskList.msg"
  "msg/TaskSchedule.msg"
  "msg/Track.msg"
  "msg/TrackArray.msg"
  "msg/Zones.msg"
  "msg/UnvisitedPointsArray.msg"
  "msg/MultipointProgress.msg"
  # Srv
  "srv/ChooseTarget.srv"
  "srv/ClearPath.srv"
  "srv/ClearPathIdx.srv"
  "srv/ClearTarget.srv"
  "srv/CmdVelInput.srv"
  "srv/DrawMultiPolygons.srv"
  # "srv/edge_info.srv" #is an invalid message name.
  # "srv/get_graph_plan.srv" #is an invalid message name.
  "srv/GetDecimatedPlan.srv"
  "srv/GetPlanLength.srv"
  "srv/GetPlanLengthSimple.srv"
  "srv/GetReachableSubplan.srv"
  "srv/GetSpeed.srv"
  "srv/GetTaskType.srv"
  "srv/LaunchExists.srv"
  "srv/MarkPath.srv"
  # "srv/pathdistance.srv"
  "srv/SetPlanDecimation.srv"
  "srv/SetGoalTolerance.srv"
  "srv/GetGoalTolerance.srv"
  "srv/SetInflationLayer.srv"
  "srv/SetSpeed.srv"
  "srv/SetVelocity.srv"
  "srv/SpeedZones.srv"
  "srv/StartLaunch.srv"
  "srv/StartZoneCoverageStats.srv"
  "srv/StopLaunch.srv"
  "srv/StringArrayTrigger.srv"
  "srv/StringTrigger.srv"
  "srv/Uint8.srv"
  "srv/Uint8ArrayStringTrigger.srv"
  "srv/HardwareStates.srv"
  "srv/PoseWithCovarianceStamped.srv"
  "srv/Reset.srv"
  "srv/LoadMap.srv"
  "srv/MFNSaveTransitPoint.srv"
  "srv/MFNSaveMapNames.srv"
  "srv/MFNGetMapId.srv"
  "srv/StopReconfig.srv"
  "srv/TeleopPlanner.srv"
  "srv/ZonePolygon.srv"
  "srv/ThrottleSpeed.srv"
  "srv/MultipointPath.srv"
  "srv/UniversalHandlerRunTask.srv"
  "srv/GetTaskDurationEstimate.srv"
  "srv/BackupConfig.srv"
  "srv/RestoreConfig.srv"
  "srv/SetFloat64.srv"
  "srv/AprilTagBundles.srv"
  "srv/AprilTagStandalone.srv"
  "srv/TagOffset.srv"
  # Actions
  "action/RunTaskList.action"
  "action/UnifiedTask.action"
  # Deps
  DEPENDENCIES std_msgs geometry_msgs nav_msgs diagnostic_msgs sensor_msgs
)

ament_export_dependencies(rosidl_default_runtime std_msgs geometry_msgs)

ament_package()

option(CONFIGURE_DEBIAN_PACKAGE "Configure debian package" OFF)
if (CONFIGURE_DEBIAN_PACKAGE)
  string(REGEX MATCH "^.*/seirios_ros" SEIRIOS_ROOT_DIR ${PROJECT_SOURCE_DIR})
  include(${SEIRIOS_ROOT_DIR}/debian.cmake)
endif()
