cmake_minimum_required (VERSION 3.8.1)
# imgui library: imgui is build by default, but you can
# provide your own version by setting QTIMGUI_BUILD_IMGUI to OFF
option(QTIMGUI_BUILD_IMGUI "Use imgui provided as qtimgui submodule" ON)
if (QTIMGUI_BUILD_IMGUI)
    add_library(imgui
            STATIC
            dependencies/imgui/imconfig.h
            dependencies/imgui/imgui.cpp
            dependencies/imgui/imgui.h
            dependencies/imgui/imgui_demo.cpp
            dependencies/imgui/imgui_draw.cpp
            dependencies/imgui/imgui_internal.h
            dependencies/imgui/imgui_widgets.cpp
            dependencies/imgui/imgui_tables.cpp
            dependencies/imgui/imstb_rectpack.h
            dependencies/imgui/imstb_textedit.h
            dependencies/imgui/imstb_truetype.h
            )
    target_include_directories(imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/dependencies/imgui)
endif(QTIMGUI_BUILD_IMGUI)

# implot library: implot is build by default, but you can
# provide your own version by setting QTIMGUI_BUILD_IMPLOT to OFF
option(QTIMGUI_BUILD_IMPLOT "Use implot provided as qtimgui submodule" ON)
if (QTIMGUI_BUILD_IMPLOT)
    add_library(implot
            STATIC
            dependencies/implot/implot.h
            dependencies/implot/implot.cpp
            dependencies/implot/implot_internal.h
            dependencies/implot/implot_items.cpp
            dependencies/implot/implot_demo.cpp
            )

    target_include_directories(implot PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/dependencies/implot)
    target_link_libraries(implot PUBLIC imgui)

endif(QTIMGUI_BUILD_IMPLOT)
