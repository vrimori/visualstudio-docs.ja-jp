---
title: WriteLinesToFile タスク | Microsoft Docs
ms.custom: ''
ms.date: 09/20/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 909c35ca889295385cae98d51a81b22b4f7eb5d8
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228839"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile タスク
指定したアイテムのパスを指定したテキスト ファイルに書き込みます。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `WriteLinestoFile` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`File`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> 項目を書き込むファイルを指定します。|  
|`Lines`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> ファイルに書き込む項目を指定します。|  
|`Overwrite`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、タスクはファイル内の既存のコンテンツをすべて上書きします。|  
|`Encoding`|省略可能な `String` 型のパラメーターです。<br /><br /> 文字エンコードを選択します。たとえば、"Unicode" を選択します。  「 <xref:System.Text.Encoding>」も参照してください。|  
|`WriteOnlyWhenDifferent`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、ターゲット ファイルを指定すると、そのターゲット ファイルが最初に読み取られ、タスクによって書き込まれる内容と比較されます。 等しい場合、ファイルはディスクに書き込まれず、タイムスタンプが保持されます。|  

## <a name="remarks"></a>コメント  
 `Overwrite` が `true` の場合、新しいファイルを作成し、内容をそのファイルに書き込んだ後、ファイルを閉じます。 既存のターゲット ファイルは上書きされます。 `Overwrite` が `false` の場合、ファイルにコンテンツを追加します。ターゲット ファイルがまだ存在しない場合は、ファイルを作成します。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`WriteLinesToFile` タスクを利用し、`MyTextFile` 項目コレクションにより指定されたファイルに、`MyItems` 項目コレクションの項目のパスを書き込みます。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```

この例では、改行が埋め込まれたプロパティを使用して、複数行のテキスト ファイルを記述します。 `Lines` のエントリに改行文字が埋め込まれている場合、出力ファイルに新しい行が含まれます。 このようにして、複数行プロパティを参照することができます。

```xml  
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)
