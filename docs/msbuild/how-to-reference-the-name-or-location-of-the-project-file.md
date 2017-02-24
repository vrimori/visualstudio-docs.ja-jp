---
title: "方法: プロジェクト ファイルの名前または場所を参照する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: cd4ed0d5d7df332bd1f49edd5989f56a09293c44

---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>方法 : プロジェクト ファイルの名前または場所を参照する
独自のプロパティを作成することなく、プロジェクト ファイル自体のプロジェクトの名前または場所を使用できます。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、プロジェクトのファイル名とプロジェクトに関連するその他のプロパティを参照する、予約済みのプロパティを提供します。 予約済みのプロパティの詳細については、「[MSBuild の予約済みおよび既知のプロパティ](../msbuild/msbuild-reserved-and-well-known-properties.md)」を参照してください。  
  
## <a name="using-the-msbuildprojectname-property"></a>MSBuildProjectName プロパティの使用  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、毎回定義することなくプロジェクト ファイルで使用できる、いくつかの予約済みプロパティを提供します。 たとえば、予約済みプロパティ `MSBuildProjectName` はプロジェクト ファイル名への参照を提供します。  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>MSBuildProjectName プロパティを使用するには  
  
-   他のすべてのプロパティの場合と同様に、$() 表記でプロジェクト ファイルのプロパティを参照します。 例:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 予約済みのプロパティを使用する利点は、プロジェクト ファイル名への変更がすべて自動的に組み込まれることです。 次回プロジェクトをビルドするとき、出力ファイルに新しい名前が付けられ、追加の操作は必要ありません。  
  
> [!NOTE]
>  予約済みのプロパティは、プロジェクト ファイルで再定義できません。  
  
## <a name="example"></a>例  
 次の例では、プロジェクト ファイルは出力の名前を指定する予約済みのプロパティとして、プロジェクト名を参照します。  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
[MSBuild](../msbuild/msbuild.md)  
 [MSBuild の予約済みおよび既知のプロパティ](../msbuild/msbuild-reserved-and-well-known-properties.md)


<!--HONumber=Feb17_HO4-->


