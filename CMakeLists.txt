cmake_minimum_required(VERSION 3.10.0)
project(GitPowerWorktree VERSION 0.1.0 LANGUAGES C CXX)

if (MINGW)
    message("MinGW detected")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static-libgcc -static-libstdc++")
endif()

# src/include配下のヘッダーファイルをインクルードパスに追加
include_directories(${CMAKE_SOURCE_DIR}/src/includes)

# 実行ファイルの作成とライブラリのリンク
add_executable(git-pt)
# 実行ファイルの出力先を設定
set_target_properties(git-pt PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# ソースファイルの関連付け
target_sources(git-pt
    PRIVATE
        src/main.cpp
)
