project(ffplay)

find_package(FFMPEG REQUIRED)
find_package(SDL2 CONFIG REQUIRED)
include_directories(${FFMPEG_INCLUDE_DIRS})

add_executable(ffplay ffplay.c opt_common.c cmdutils.c ffplay_renderer.c)
target_link_libraries(ffplay PRIVATE ${FFMPEG_LIBRARIES})
target_link_libraries(ffplay PRIVATE $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main> $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>)