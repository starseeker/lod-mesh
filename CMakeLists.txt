project(LOD)

cmake_minimum_required(VERSION 3.12)

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_library(M_LIBRARY m)

set(lod_srcs
	aabb.c
	draw_string.c
	main.c
	mesh.c
	octree.c
	shader.c
	timer.c
	vfc.c
	view_params.c
	)

if (OPENGL_opengl_LIBRARY)
	set(OPENGL_LIBS ${OPENGL_opengl_LIBRARY})
endif (OPENGL_opengl_LIBRARY)
if (OPENGL_gl_LIBRARY)
	set(OPENGL_LIBS ${OPENGL_gl_LIBRARY})
endif (OPENGL_gl_LIBRARY)

add_definitions(-g)

add_executable(lod-mesh ${lod_srcs})
target_link_libraries(lod-mesh ${OPENGL_LIBS} ${GLUT_glut_LIBRARY} ${M_LIBRARY})

