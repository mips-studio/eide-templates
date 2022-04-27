## 说明

此处作为 eide 的公共远程模板仓库，使用 eide 的 `从远程模板创建项目` 功能时，将在此仓库中获取可用的项目模板

![image](https://user-images.githubusercontent.com/43022536/165442017-dc7f8377-f533-422d-b56a-bef5c5ef2cd9.png)

## 如何贡献项目模板？

- **克隆仓库**：在 github 上 fork 仓库到自己的账号中，并在本地使用 `git clone` 克隆 fork 后的仓库

- **生成模板**：在 vscode 上打开你想要分享的 eide 项目，使用 [导出 eide 项目模板](https://docs.em-ide.com/#/zh-cn/export_project?id=%e5%af%bc%e5%87%ba-eide-%e6%a8%a1%e6%9d%bf) 功能，将在项目根目录下生成一个 `.ept` 文件

- **检查模板**：使用 eide 的 `从本地模板创建项目` 功能，选择上一步生成的模板文件，新建一个工程，检查工程是否可用

- **添加文件**：将 `ept` 文件复制到本地仓库中

- **注册模板**：修改索引文件：`index.json`，将模板的信息（文件名，分类，版本号，可读名称，作者名称...）注册到其中，可参考该 [pull request 示例](https://github.com/github0null/eide-templates/pull/1/commits/8994e21c7b0898f228b45649859b6a54eef1566e)

- **推送仓库**：将更改后的本地仓库推送至 github 远程仓库中，然后创建 `pull request`，请求合并至主仓库，合并完成之后即可在 vscode 上直接使用

## 模板索引格式

模板索引文件 index.json 存放了所有的模板的信息，该文件是一个 `TemplateIndexDef` 类型的 json 对象，定义如下：

```typescript

// 模板索引
export interface TemplateIndexDef {
    category_map: { [name: string]: CategoryInfo };
    template_list: TemplateInfo[];
}

// 模板分类
export interface CategoryInfo {
    display_name: string;   // 用于显示的名称
    description: string;    // 简短的描述
}

// 模板信息
export interface TemplateInfo {

    file_name: string;          // 模板文件名

    display_name: string;       // 用于显示的名称

    category: string[];         // 模板所属的分类

    version: string;            // 版本

    author: string | undefined; // 作者名称
}

```
