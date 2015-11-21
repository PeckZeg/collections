Sublime3 支持编译 C++ 11
=======================

1. 新建一个 Build System (`Tools` -> `Build System` -> `new Build System`)
2. 将如下配置文件塞入窗口

    ```json
{
    "cmd": ["clang++", "${file}","-std=c++11", "-stdlib=libc++", "-o", "${file_path}/${file_base_name}"],
    "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
    "working_dir": "${file_path}",
    "selector": "source.c, source.c++",
 
    "variants":
    [
        {
            "name": "Run",
            "cmd": ["bash", "-c", "clang++  '${file}' -std=c++11 -stdlib=libc++ -o '${file_path}/${file_base_name}' && '${file_path}/${file_base_name}'"]
        }
    ]
}
    ```

3. 保存为 `C++11.sublime-build`