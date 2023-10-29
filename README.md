# Instrukcja/dokumentacja co robiłem i z czego korzystałem:

- https://www.glfw.org/docs/3.3/build_guide.html#build_link_cmake_package. Tutaj jest informacja jak dodać do swojego projektu cmake budowanie biblioteki glfw z kodu źródłowego. Jest też opcja użycia prekompilowanych źródeł, ale trzeba na pewno trafić z kompilatorem, więc ja wybrałem opcję zbudowania u siebie lokalnie.
- Wcześniej zrobiłem clone (submodule) kodu biblioteki glfw do folderu `/lib`. (https://github.com/glfw/glfw)
- OpenGL też jest potrzebny w cmake (jest w instrukcji z pierwszego linku do GLFW)
- zrobiłem clone (submodule) repo imgui do folderu libs (https://github.com/ocornut/imgui/)
- Biblioteka imgui nie posiada własnego pliku CMakeLists.txt. Zatem plik CMakeLists.txt z /lib zawiera add_library z imgui,
tam dodane są pliki źródłowe z głównego folderu oraz dwa pliki (glfw i opengl) z folderu imgui/backends. W include directories dla imgui dodałem główny folder oraz folder backends. Dalej jest `target_link_libraries(imgui glfw)`. W ostatniej linii jest `add_subdirectories` z biblioteką glfw.
- W głównym pliku cmake dodałem link imgui do głównego projektu. Wygenerowałem projekt używając Ninja i mingw (w folderze build `cmake .. -G Ninja`).
- Pozbywałem się błędów linkowania dodając kolejne pliki cpp których brakowało.
