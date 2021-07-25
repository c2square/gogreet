# ”0 项目介绍
这是一个go module学习项目，主要用来学习Go语言的项目架构，主要来自https://golang.org/doc/

# 1 创建并引用一个go module
1. 创建文件夹

2. 执行`go mod init example.com/yourmod`

    > 此处创建了一个`go.mod`文件来追踪这个`module`的依赖项，类似于`maven`。
    >
    > `go.mod`里面还包括了这个`module`的名称和支持的go版本

3. 创建并编写`yourmod.go`文件

    ```go
    package yourmod
    
    import "fmt"
    
    // Hello returns a greeting for the named person.
    func Hello(name string) string {
        // Return a greeting that embeds the name in a message.
        message := fmt.Sprintf("Hi, %v. Welcome!", name)
        return message
    }
    ```

    `yourmod`模块构建完成，下面开始引用

4. 在其他的模块里可以`import`刚才写的模块

    ```go
    import (
        "fmt"
    
        "example.com/yourmod"
    )
    ```

5. 如果是本地项目，远程没有，则可以利用`go mod`工具进行替换

    ```shell
    # 假设项目目录为
    # <home>/
    #  |-- yourmod/
    #  |-- callProject/
    $ go mod edit -replace example.com/yourmod=../yourmod
    ```

6. 完成后执行`go mod tidy`来同步依赖项

7. 之后就可以执行`go run .`来执行程序了

