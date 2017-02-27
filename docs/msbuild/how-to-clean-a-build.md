---
title: "方法 : ビルドをクリーンする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ディレクトリ [.NET Framework], 出力アイテムの"
  - "Exec タスク [MSBuild]"
  - "MSBuild, クリーン (ビルドを)"
  - "出力, 削除 (項目を)"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 方法 : ビルドをクリーンする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ビルドをクリーンすると、プロジェクト ファイルとコンポーネント ファイルを残して、中間ファイルや出力ファイルがすべて削除されます。  このプロジェクト ファイルおよびコンポーネント ファイルから、中間ファイルと出力ファイルを新たにビルドできます。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に用意されている一般的なタスクのライブラリには、システム コマンドを実行するための [Exec](../msbuild/exec-task.md) タスクが含まれています。  タスクのライブラリの詳細については、「[Task Reference](../msbuild/msbuild-task-reference.md)」を参照してください。  
  
## 出力項目用ディレクトリの作成  
 既定では、プロジェクトをコンパイルして作成される .exe ファイルは、プロジェクト ファイルやソース ファイルと同じディレクトリに格納されます。  しかし、出力項目は別個のディレクトリに作成するのが一般的です。  
  
#### 出力項目用ディレクトリを作成するには  
  
1.  ディレクトリの場所と名前を定義するには `Property` 要素を使用します。  たとえば、プロジェクトやソースファイルを格納するディレクトリに、`BuiltApp` という名前のディレクトリを作成するには、次のようにします。  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  ディレクトリが存在しない場合は、[MakeDir](../msbuild/makedir-task.md) タスクを使用してディレクトリを作成します。  次に例を示します。  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## 出力項目の削除  
 新しい中間ファイルや出力ファイルを作成する前に、既存の中間ファイルと出力ファイルはすべて削除しておきます。  ディレクトリと、そのディレクトリに格納されたすべてのファイルおよびディレクトリをディスクから削除するには、[RemoveDir](../msbuild/removedir-task.md) タスクを使用します。  
  
#### ディレクトリと、そのディレクトリに格納されたすべてのファイルを削除するには  
  
-   `RemoveDir` タスクを使用してディレクトリを削除します。  次に例を示します。  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## 使用例  
 次のコード例に示すプロジェクトには、`RemoveDir` タスクを使用して、ディレクトリとそのディレクトリに格納されたすべてのファイルおよびディレクトリを削除する新しいターゲット `Clean` が含まれています。  また、この例では、出力項目用の別のディレクトリが `Compile` ターゲットによって作成されます。このディレクトリは、ビルドがクリーンされたときに削除されます。  
  
 `Compile` は既定のターゲットとして定義されているため、別のターゲットを指定しない限り自動的に使用されます。  別のターゲットを指定する場合は、コマンド ライン スイッチ **\/target** を使用します。  次に例を示します。  
  
 `msbuild <file name>.proj /target:Clean`  
  
 **\/target** スイッチは、**\/t** のように省略でき、複数のターゲットを指定することもできます。  たとえば、ターゲット `Clean` と `Compile` を順に使用する場合は、次のように入力します。  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## 参照  
 [Exec Task](../msbuild/exec-task.md)   
 [MakeDir Task](../msbuild/makedir-task.md)   
 [RemoveDir Task](../msbuild/removedir-task.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [ターゲット](../msbuild/msbuild-targets.md)