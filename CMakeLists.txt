cmake_minimum_required(VERSION 3.10.0)
project(GitPowerWorktree VERSION 0.1.0 LANGUAGES C CXX)

if (MINGW)
    message("MinGW detected")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static-libgcc -static-libstdc++")
endif()

# srcディレクトリ配下の全cppファイルを自動で追加
file(GLOB_RECURSE SRC_FILES src/*.cpp)

# src/include配下のヘッダーファイルをインクルードパスに追加
include_directories(${CMAKE_SOURCE_DIR}/src/includes)

# 取得できたファイルの表示（デバッグ用）
foreach(file ${SRC_FILES})
    message(STATUS "Found source file: ${file}")
endforeach()


# 実行ファイルの作成とライブラリのリンク
add_executable(git-pt ${SRC_FILES})
