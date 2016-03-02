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
add_definitions(-DGLEW_STATIC) # tell glew headers we are static linking with glew

fips_begin_lib(nanovg)
    fips_include_directories(nanovg/src)
    fips_src(nanovg/src)
fips_end_lib()

if (NOT FIPS_IMPORT)
    if (FIPS_MACOS OR FIPS_LINUX OR FIPS_WINDOWS)
        fips_begin_app(example_gl2 cmdline)
            fips_include_directories(nanovg/src nanovg/example)
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
            fips_include_directories(nanovg/src nanovg/example)
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
        fips_begin_app(example_fbo cmdline)
            fips_include_directories(nanovg/src nanovg/example)
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
        fips_begin_app(example_gl2_msaa cmdline)
            add_definitions(-DDEMO_MSAA)
            fips_include_directories(nanovg/src nanovg/example)
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
        fips_begin_app(example_gl3_msaa cmdline)
            add_definitions(-DDEMO_MSAA)
            fips_include_directories(nanovg/src nanovg/example)
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
    endif()
endif()


if (NOT FIPS_IMPORT)
    fips_finish()
endif()

