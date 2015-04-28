#compile core
add_subdirectory(LMS/lms)
#Add shared headers
file(GLOB_RECURSE SHARED_HEADER **/CMakeSharedHeaders.txt)
if (SHARED_HEADER)
        foreach(filepath ${SHARED_HEADER})
                get_filename_component(FOLDER ${filepath} DIRECTORY)
                include_directories(${FOLDER})
                include("${FOLDER}/CMakeSharedHeaders.txt")
	endforeach()
endif()
#compile libs/modules
add_subdirectory(external)