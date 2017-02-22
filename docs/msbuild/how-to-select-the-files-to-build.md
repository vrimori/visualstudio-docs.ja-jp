---
title: "方法: ビルドするファイルを選択する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Include 属性 [MSBuild]"
  - "MSBuild, インクルード (ファイルを)"
  - "MSBuild, ワイルドカード"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法: ビルドするファイルを選択する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

複数のファイルから成るプロジェクトをビルドするとき、プロジェクト ファイルで個々のファイルを指定する以外に、ワイルドカードを使用して 1 つのディレクトリまたは入れ子になった複数のディレクトリのファイルをすべてインクルードできます。  
  
## 入力の指定  
 ビルドの入力ファイルは項目によって表されます。  項目の詳細については、「[項目](../msbuild/msbuild-items.md)」を参照してください。  
  
 ビルド対象のファイルをインクルードするには、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] のプロジェクト ファイルで、これらのファイルを項目のリストに追加する必要があります。  複数のファイルを項目のリストに追加するには、ファイルを個別にインクルードするか、ワイルドカードを使用して複数のファイルを一度にインクルードします。  
  
#### 項目を個別に宣言するには  
  
-   `Include` 属性を次のように使用します。  
  
     `<CSFile Include="form1.cs"/>`  
  
     または  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  項目のコレクションの項目がプロジェクト ファイルと同じディレクトリに存在する場合は、項目の完全パスまたは相対パスを指定します。  たとえば、`Include="..\..\form2.cs"` となります。  
  
#### 複数の項目を宣言するには  
  
-   `Include` 属性を次のように使用します。  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     または  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## 入力ファイルをワイルドカードで指定する  
 ワイルドカードを使用して、サブディレクトリからビルドの入力対象となるすべてのファイルまたは特定のファイルのみを再帰的にインクルードすることもできます。  ワイルドカードの詳細については、「[項目](../msbuild/msbuild-items.md)」を参照してください。  
  
 ここでは、プロジェクト ファイルが Project ディレクトリに置かれているプロジェクトを例にとってみます。グラフィックス ファイルが次のディレクトリおよびサブディレクトリに置かれています。  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### Images ディレクトリとサブディレクトリに存在するすべての .jpg ファイルをインクルードするには  
  
-   次の `Include` 属性を使用します。  
  
     `Include="Images\**\*.jpg"`  
  
#### "img" で始まるすべての .jpg ファイルをインクルードするには  
  
-   次の `Include` 属性を使用します。  
  
     `Include="Images\**\img*.jpg"`  
  
#### "jpgs" で終わるディレクトリ内のすべてのファイルをインクルードするには  
  
-   次のいずれかの `Include` 属性を使用します。  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     または  
  
     `Include="Images\**\*jpgs\*"`  
  
## 項目をタスクに渡す  
 プロジェクト ファイルでは、タスクに @\(\) 表記を使用することにより、ビルドの入力対象として項目のリスト全体を指定できます。  この表記は、すべてのファイルを個別に指定した場合でも、ワイルドカードを使った場合でも使用できます。  
  
#### すべての Visual C\# ファイルまたはすべての Visual Basic ファイルを入力として使用するには  
  
-   `Include` 属性を次のように使用します。  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     または  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  ビルドの入力ファイルを複数指定する場合、ワイルドカードは項目に対して使用する必要があります。[Csc](../msbuild/csc-task.md) や [Vbc](../msbuild/vbc-task.md) など、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクの `Sources` 属性を使用して入力ファイルを指定することはできません。  プロジェクト ファイルでは、次の例のような使い方はできません。  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## 使用例  
 すべての入力ファイルを個別にインクルードするプロジェクトを次のコード例に示します。  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## 使用例  
 ワイルドカードを使用してすべての .cs ファイルをインクルードするコード例を次に示します。  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## 参照  
 [方法: ビルドからファイルを除外する](../msbuild/how-to-exclude-files-from-the-build.md)   
 [項目](../msbuild/msbuild-items.md)