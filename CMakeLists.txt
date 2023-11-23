# Copyright 2018 Peter Dimov
# Copyright 2018 Andrey Semashev
# Distributed under the Boost Software License, Version 1.0.
# See accompanying file LICENSE_1_0.txt or copy at https://www.boost.org/LICENSE_1_0.txt

if(NOT DEFINED IDF_TARGET)

cmake_minimum_required(VERSION 3.5...3.20)

project(boost_iterator VERSION "${BOOST_SUPERPROJECT_VERSION}" LANGUAGES CXX)

add_library(boost_iterator INTERFACE)
add_library(Boost::iterator ALIAS boost_iterator)

target_include_directories(boost_iterator INTERFACE include)

target_link_libraries(boost_iterator
    INTERFACE
        Boost::assert
        Boost::concept_check
        Boost::config
        Boost::conversion
        Boost::core
        Boost::detail
        Boost::function_types
        Boost::fusion
        Boost::mpl
        Boost::optional
        Boost::smart_ptr
        Boost::static_assert
        Boost::type_traits
        Boost::utility
)

else()

FILE(GLOB_RECURSE headers include/*.h include/*.hpp)

idf_component_register(
    SRCS
        ${headers}
    INCLUDE_DIRS
        include
    REQUIRES
        boost_assert
        boost_concept_check
        boost_config
        boost_conversion
        boost_core
        boost_detail
        boost_function_types
        boost_fusion
        boost_mpl
        boost_optional
        boost_smart_ptr
        boost_static_assert
        boost_type_traits
        boost_utility
)

endif()
