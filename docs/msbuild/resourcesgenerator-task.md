---
title: "ResourcesGenerator タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: a698aec32ff5ec093fe2cff2dc0533f6e364be21
ms.contentlocale: ja-jp
ms.lasthandoff: 02/22/2017

---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator タスク
<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> タスクは、1 つ以上のリソース (.jpg、.ico、.bmp、バイナリ形式の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]、その他の種類の拡張子) を .resources ファイルに埋め込みます。  
  
## <a name="task-parameters"></a>タスク パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`OutputPath`|必須の **String** 型のパラメーターです。<br /><br /> 出力ディレクトリのパスを指定します。 パスが絶対パスではない場合は、プロジェクトのルート ディレクトリに対する相対パスとして扱われます。|  
|`OutputResourcesFile`|必須の **ITaskItem[]** 型の出力パラメーターです。<br /><br /> 生成される .resources ファイルのパスと名前を指定します。 パスが絶対パスではない場合、.resources ファイルはプロジェクトのルート ディレクトリに対する相対パスに作成されます。|  
|`ResourcesFiles`|必須の **ITaskItem[]** 型のパラメーターです。<br /><br /> 生成される .resources ファイルに埋め込まれる 1 つ以上のリソースを指定します。|  
  
## <a name="example"></a>例  
 1 つの .bmp リソースを持つ .resources ファイルを作成する例を次に示します。 .bmp リソースは、プロジェクトのルート ディレクトリを基準にした相対ディレクトリに生成されます。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)   
 [タスク リファレンス](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション (WPF) のビルド](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
