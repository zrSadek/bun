cmake_minimum_required(VERSION 3.28)
project(sqlite3 C)

add_library(sqlite3 STATIC sqlite3.c)
target_include_directories(sqlite3 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_compile_definitions(sqlite3 PRIVATE
  "SQLITE_ENABLE_COLUMN_METADATA="
  "SQLITE_MAX_VARIABLE_NUMBER=250000"
  "SQLITE_ENABLE_RTREE=1"
  "SQLITE_ENABLE_FTS3=1"
  "SQLITE_ENABLE_FTS3_PARENTHESIS=1"
  "SQLITE_ENABLE_FTS5=1"
  "SQLITE_ENABLE_JSON1=1"
  "SQLITE_ENABLE_MATH_FUNCTIONS=1"
)

if(WIN32)
  target_compile_options(sqlite3 PRIVATE /MT /U_DLL)
endif()
