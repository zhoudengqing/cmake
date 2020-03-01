# cmake

cmake教程

## ubuntu下安装cmake

```
1. tar -zxf cmake-3.17.0-rc1.tar.gz
2. cd   cmake-3.17.0-rc1
3. ./bootstrap
4. make -j4
5. make install
```

## cmake语法介绍

```
1. cmake_minimum_required(VERSION <min>...[max]) 指定cmake的版本号，例如：cmake_minimum_required(VERSION 3.17)
2. project(PROJECT-NAME [语言]) 设置工程名 如project(test C CXX) 
3. set(SRCS a.c b.c) 定义变量或给已定义给变量赋值
4. message([<mode>] "message text" ...) 打印信息 mode:STATUS DEBUG
5. configure_file(<input> <output> [COPYONLY] [ESCAPE_QUOTES] [@ONLY] [NEWLINE_STYLE [UNIX|DOS|WIN32|LF|CRLF] ]) 将 <input> 文件里面的内容全部复制到 <output> 文件中
6. file(READ <filename> <variable>
     [OFFSET <offset>] [LIMIT <max-in>] [HEX])将文件内容读出保存到变量  
    file(STRINGS <filename> <variable> [<options>...])将文件以ASCII形式保存到变量  
    file(WRITE <filename> <content>...)
    file(APPEND <filename> <content>...)将content内容写入文件
7. find_file (<VAR> name1 [path1 path2 ...])查找name1并将查到的结果保存到变量VAR
8. find_library (<VAR> name1 [path1 path2 ...])查找库文件并保存到变量
9. find_package(<PackageName>) 查找依赖包
10. find_path (<VAR> name1 [path1 path2 ...])查找文件的路径
11. foreach(<loop_var> <items>)  
            <commands>  
    endforeach()循环语句
12. function(<name> [<arg1> ...])  
        <commands>  
    endfunction()定义函数方便后面使用
13. if(<condition>)  
        <commands>  
    elseif(<condition>) # optional block, can be repeated  
        <commands>  
    else()              # optional block  
        <commands>  
    endif()条件判断语句
14. list(LENGTH <list><output variable>)  
    list(GET <list> <elementindex> [<element index> ...]<output variable>)  
    list(APPEND <list><element> [<element> ...])  
    list(FIND <list> <value><output variable>)  
    list(INSERT <list><element_index> <element> [<element> ...])  
    list(REMOVE_ITEM <list> <value>[<value> ...])  
    list(REMOVE_AT <list><index> [<index> ...])  
    list(REMOVE_DUPLICATES <list>)  
    list(REVERSE <list>)  
    list(SORT <list>)  
    LENGTH：返回list的长度  
    GET：返回list中index的element到value中  
    APPEND：添加新element到list中  
    FIND：返回list中element的index，没有找到返回-1  
    INSERT：将新element插入到list中index的位置  
    REMOVE_ITEM：从list中删除某个element  
    REMOVE_AT：从list中删除指定index的element  
    REMOVE_DUPLICATES：从list中删除重复的element  
    REVERSE：将list的内容反转  
    SORT：将list按字母顺序排序  
15. option(<variable> "<help_text>" [value]) 选项开关  
    option(TEST_DEBUG "option for debug" OFF)  
    if (TEST_DEBUG)  
        add_definitions(-DTEST_DEBUG)  
    endif()  
16. string(FIND <string> <substring> <out-var> [...])  
    string(REPLACE <match-string> <replace-string> <out-var> <input>...)  
    string(REGEX MATCH <match-regex> <out-var> <input>...)  
    string(REGEX MATCHALL <match-regex> <out-var> <input>...)  
    string(REGEX REPLACE <match-regex> <replace-expr> <out-var> <input>...)  
    string(APPEND <string-var> [<input>...])  
    string(PREPEND <string-var> [<input>...])  
    string(CONCAT <out-var> [<input>...])  
    string(JOIN <glue> <out-var> [<input>...])  
    string(TOLOWER <string> <out-var>)  
    string(TOUPPER <string> <out-var>)  
    string(LENGTH <string> <out-var>)  
    string(SUBSTRING <string> <begin> <length> <out-var>)  
    string(STRIP <string> <out-var>)  
    string(GENEX_STRIP <string> <out-var>)  
    string(REPEAT <string> <count> <out-var>)  
    string(COMPARE <op> <string1> <string2> <out-var>)  
    string(<HASH> <out-var> <input>)  
    string(ASCII <number>... <out-var>)  
    string(CONFIGURE <string> <out-var> [...])  
    string(MAKE_C_IDENTIFIER <string> <out-var>)  
    string(RANDOM [<option>...] <out-var>)  
    string(TIMESTAMP <out-var> [<format string>] [UTC])  
    string(UUID <out-var> ...)  
    一系列的字符串操作函数
17. while(<condition>)  
        <commands>  
    endwhile()  
    while循环语句
18. add_executable(app two.cpp three.h) 生成可执行目标app
19. add_library(one STATIC two.cpp three.h) 生成静态库文件one 类型有STATIC/SHARED等
20. add_subdirectory(source_dir [binary_dir] [EXCLUDE_FROM_ALL]) 将指定的文件夹加到build任务列表中
21. aux_source_directory(<dir> <variable>) 搜集所有在指定路径下的源文件的文件名，将输出结果列表储存在指定的变量中
22. include_directories([AFTER|BEFORE] [SYSTEM] dir1 [dir2 ...]) 添加头文件路径
23. install(TARGETS <target>... [...])  
    install({FILES | PROGRAMS} <file>... [...])  
    install(DIRECTORY <dir>... [...])  
    install(SCRIPT <file> [...])  
    install(CODE <code> [...])  
    install(EXPORT <export-name> [...])  
24. target_include_directories(app PUBLIC include)给目标文件添加头文件路径
25. target_link_libraries(app one) 给目标文件链接库文件
```
