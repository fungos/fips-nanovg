#
# project: fips-nanovg
#

if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-nanovg)
endif()

add_definitions(-DNANOVG_GLEW)
add_definitions(-DDEMO_MSAA)

fips_begin_lib(nanovg)
    include_directories(nanovg/src)
    fips_dir(nanovg/src)
    fips_files(
        fontstash.h
        nanovg.c
        nanovg.h
        nanovg_gl.h
        nanovg_gl_utils.h
        stb_image.h
        stb_truetype.h
    )
fips_end_lib()

if (FIPS_MACOS OR FIPS_LINUX OR FIPS_WINDOWS)
    fips_begin_app(example_gl2 cmdline)
        include_directories(nanovg/src nanovg/example)
        fips_dir(nanovg/example)
        fips_files(example_gl2.c demo.c demo.h perf.c perf.h stb_image_write.h)
        fips_deps(nanovg GLEW glfw3)

        if (FIPS_WINDOWS)
            fips_libs(opengl32)
        endif()

        if (FIPS_LINUX)
            fips_libs(X11 Xrandr Xi Xinerama Xxf86vm Xcursor GL m)
        endif()

        if (FIPS_MACOS)
            fips_libs(m)
        endif()
    fips_end_app()
    fips_begin_app(example_gl3 cmdline)
        include_directories(nanovg/src nanovg/example)
        fips_dir(nanovg/example)
        fips_files(example_gl3.c demo.c demo.h perf.c perf.h stb_image_write.h)
        fips_deps(nanovg GLEW glfw3)

        if (FIPS_WINDOWS)
            fips_libs(opengl32)
        endif()

        if (FIPS_LINUX)
            fips_libs(X11 Xrandr Xi Xinerama Xxf86vm Xcursor GL m)
        endif()

        if (FIPS_MACOS)
            fips_libs(m)
        endif()
    fips_end_app()
    fips_begin_app(example_gles2 cmdline)
        include_directories(nanovg/src nanovg/example)
        fips_dir(nanovg/example)
        fips_files(example_gles2.c demo.c demo.h perf.c perf.h stb_image_write.h)
        fips_deps(nanovg GLEW glfw3)

        if (FIPS_WINDOWS)
            fips_libs(opengl32)
        endif()

        if (FIPS_LINUX)
            fips_libs(X11 Xrandr Xi Xinerama Xxf86vm Xcursor GL m)
        endif()

        if (FIPS_MACOS)
            fips_libs(m)
        endif()
    fips_end_app()
    fips_begin_app(example_gles3 cmdline)
        include_directories(nanovg/src nanovg/example)
        fips_dir(nanovg/example)
        fips_files(example_gles3.c demo.c demo.h perf.c perf.h stb_image_write.h)
        fips_deps(nanovg GLEW glfw3)

        if (FIPS_WINDOWS)
            fips_libs(opengl32)
        endif()

        if (FIPS_LINUX)
            fips_libs(X11 Xrandr Xi Xinerama Xxf86vm Xcursor GL m)
        endif()

        if (FIPS_MACOS)
            fips_libs(m)
        endif()
    fips_end_app()
    fips_begin_app(example_fbo cmdline)
        include_directories(nanovg/src nanovg/example)
        fips_dir(nanovg/example)
        fips_files(example_fbo.c demo.c demo.h perf.c perf.h stb_image_write.h)
        fips_deps(nanovg GLEW glfw3)

        if (FIPS_WINDOWS)
            fips_libs(opengl32)
        endif()

        if (FIPS_LINUX)
            fips_libs(X11 Xrandr Xi Xinerama Xxf86vm Xcursor GL m)
        endif()

        if (FIPS_MACOS)
            fips_libs(m)
        endif()
    fips_end_app()
endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()

