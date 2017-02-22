---
title: "MSBuild Conditional Constructs | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Choose> Element [MSBuild]"
  - "Choose Element [MSBuild]"
  - "conditional constructs [MSBuild]"
  - "MSBuild, conditional constructs"
  - "<When> Element [MSBuild]"
  - "<Otherwise> Element [MSBuild]"
  - "Otherwise Element [MSBuild]"
  - "When Element [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Conditional Constructs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] には、[Choose](../msbuild/choose-element-msbuild.md)、[When](../msbuild/when-element-msbuild.md)、[Otherwise](../msbuild/otherwise-element-msbuild.md) の各要素に or 処理の機構が用意されています。  
  
## Choose 要素の使用  
 `Choose` 要素は、`Condition` 属性を持つ一連の `When` 要素で構成され、`true` と評価されるまで、上から下へ順番にテストされます。  複数の `When` 要素が `true` と評価される場合は、最初の要素だけが使用されます。  `Otherwise` 要素が存在する場合、`When` 要素の条件がどれも `true` と評価されなかった場合に、この要素が評価されます。  
  
 `Choose` 要素は、`Project`、`When`、`Otherwise` の各要素の子要素として使用できます。  `When` および `Otherwise` 要素には、`ItemGroup`、`PropertyGroup`、または `Choose` 子要素を設定できます  
  
## 使用例  
 or 処理で `Choose` 要素および `When` 要素を使用する例を次に示します。  プロジェクトのプロパティおよび項目は、`Configuration` プロパティの値に応じて設定されます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## 参照  
 [Choose Element \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [When Element \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Otherwise Element \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)