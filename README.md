Задание 1

cd Green-Ace/workspace/TimpLab3

git clone https://github.com/tp-labs/lab03.git

cd lab03/formatter_lib

cat >> CMakeLists.txt << EOF

cmake_minimum_required(VERSION 3.10)

project(formatter)

set(CMAKE_CXX_STANDARD 20)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(formatter STATIC \${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)

include_directories(\${CMAKE_CURRENT_SOURCE_DIR})

EOF

cmake -H. -B_build



![изображение](https://user-images.githubusercontent.com/112771063/223804284-4c3d99d8-4771-4e4f-be3f-693d3109192d.png)



cmake --build _build



![изображение](https://user-images.githubusercontent.com/112771063/223804811-af8f6ee2-303c-447c-85f7-b26899020d7e.png)


Задание 2

cd Green-Ace/workspace/TimpLab3/lab03/formatter_ex_lib

cat >> CMakeLists.txt << EOF

cmake_minimum_required(VERSION 3.10)

project(formatter_ex)
  
set(CMAKE_CXX_STANDARD 20)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(formatter_ex STATIC /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_ex_lib/formatter_ex.cpp)

include_directories(\${CMAKE_CURRENT_SOURCE_DIR})

include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib)

target_link_libraries(formatter_ex formatter)

EOF

cmake -H. -B_build





![изображение](https://user-images.githubusercontent.com/112771063/223811391-fdfbaf33-10d7-4a57-b021-2e12c24504ae.png)





Задание 3

1)

cd Green-Ace/workspace/TimpLab3/lab03/hello_world_application

cat >> CMakeLists.txt <<EOF

heredoc> cmake_minimum_required(VERSION 3.10)

project(hello_world)

set(CMAKE_CXX_STANDARD 20)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(hello STATIC /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_ex_lib/formatter_ex.cpp /home/ace

/Green-Ace/workspace/TimpLab3/lab03/formatter_lib/formatter.cpp)

include_directories(/home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_ex_lib /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_lib)

add_executable(Hello /home/ace/Green-Ace/workspace/TimpLab3/lab03/hello_world_application/hello_world.cpp)

target_link_libraries(Hello hello)

EOF

cmake -H. -B_build

cmake --build _build



![изображение](https://user-images.githubusercontent.com/112771063/223831172-89b00dbf-3a13-4726-94a4-288fcad51a36.png)



_build/Hello

![изображение](https://user-images.githubusercontent.com/112771063/223832821-388fc9d4-591a-4e3d-969f-e3f97a4838bd.png)





2)


cd Green-Ace/workspace/TimpLab3/lab03/solver_application

cmake_minimum_required(VERSION 3.10)

project(solver)

set(CMAKE_CXX_STANDARD 20)
  
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(solver STATIC /home/ace/Green-Ace/workspace/TimpLab3/lab03/solver_lib/solver.cpp /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_ex_lib/formatter_ex.cpp /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_lib/formatter.cpp)


include_directories(/home/ace/Green-Ace/workspace/TimpLab3/lab03/solver_lib /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_ex_lib /home/ace/Green-Ace/workspace/TimpLab3/lab03/formatter_lib)

add_executable(Solver /home/ace/Green-Ace/workspace/TimpLab3/lab03/solver_application/equation.cpp)

target_link_libraries(Solver solver)

EOF

cmake -H. -B_build

![изображение](https://user-images.githubusercontent.com/112771063/223843341-a9c2d6fa-cafa-4bac-8f11-00a68b42a250.png)



cmake --build _build


![изображение](https://user-images.githubusercontent.com/112771063/223843402-e381c597-c9dc-4e88-b9aa-be946efd9aca.png)




_build/Solver



