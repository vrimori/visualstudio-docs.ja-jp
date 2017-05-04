---
title: "置き換え可能パラメーター | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "置き換え可能パラメーター [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 置き換え可能パラメーター"
  - "Visual Studio での SharePoint 開発, トークン"
  - "トークン [Visual Studio での SharePoint 開発]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 置き換え可能パラメーター
  SharePoint ソリューション項目に使用される値に関して、デザイン時点では実際の値がわからない場合があります。プロジェクト ファイル内では、そのような値を置き換え可能パラメーター \(*トークン*\) で指定できます。  これらは標準のテンプレート [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] トークンに似ています。  詳細については、「[テンプレート名](../ide/template-parameters.md)」を参照してください。  
  
## トークンの形式  
 トークンの先頭と末尾にはドル記号 \($\) が付いています。  配置段階でプロジェクトを SharePoint ソリューション パッケージ \(.wsp\) ファイルにパッケージ化するとき、使用されているトークンがすべて実際の値に置き換えられます。  たとえば、**$SharePoint.Package.Name$** というトークンは、"Test SharePoint Package" などの文字列に解決されます。  
  
## トークンの規則  
 トークンには次の規則が適用されます。  
  
-   トークンは行内のどの位置でも指定できます。  
  
-   トークンを複数の行にまたがって記述することはできません。  
  
-   同じトークンを同じ行、同じファイル内で繰り返し指定できます。  
  
-   同じ行に複数の異なるトークンを指定できます。  
  
 以上の規則に従っていないトークンは無視されます。その場合でも警告やエラーは発生しません。  
  
 文字列値によるトークンの置き換えは、マニフェストの変換直後に実行されます。そのため、ユーザーが編集するマニフェスト テンプレートからトークンを使用できます。  
  
### トークン名の解決  
 ほとんどの場合、トークンが含まれる場所にかかわらず、トークンは特定の値に解決されます。  ただし、トークンがパッケージまたはフィーチャーに関連している場合、トークンの値は含まれる場所によって変わります。  たとえば、フィーチャーが Package A にある場合、トークン `$SharePoint.Package.Name$` は値 "Package A" に解決されます。同じフィーチャーが Package B にある場合、`$SharePoint.Package.Name$` は "Package B" に解決されます。  
  
## トークンの一覧  
 使用できるトークンの一覧を次の表に示します。  
  
|名前|説明|  
|--------|--------|  
|$SharePoint.Project.FileName$|格納しているプロジェクト ファイルの名前 \("NewProj.csproj" など\)。|  
|$SharePoint.Project.FileNameWithoutExtension$|格納しているプロジェクト ファイルの名前から拡張子を除いた部分。  "NewProj" など。|  
|$SharePoint.Project.AssemblyFullName$|格納しているプロジェクトの出力アセンブリの表示名 \(厳密な名前\)。|  
|$SharePoint.Project.AssemblyFileName$|格納しているプロジェクトの出力アセンブリの名前。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|格納しているプロジェクトの出力アセンブリの名前からファイル名の拡張子を除いた部分。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|格納しているプロジェクトの出力アセンブリの公開キー トークンを文字列に変換した結果 \("x2" 16 進形式の 16 文字\)。|  
|$SharePoint.Package.Name$|格納しているパッケージの名前。|  
|$SharePoint.Package.FileName$|格納しているパッケージの定義ファイルの名前。|  
|$SharePoint.Package.FileNameWithoutExtension$|格納しているパッケージの定義ファイルの名前から拡張子を除いた部分。|  
|$SharePoint.Package.Id$|格納しているパッケージの SharePoint ID。  フィーチャーが複数のパッケージで使用されている場合、この値は変わります。|  
|$SharePoint.Feature.FileName$|格納しているフィーチャーの定義ファイルの名前 \(Feature1.feature など\)。|  
|$SharePoint.Feature.FileNameWithoutExtension$|フィーチャー定義ファイルの名前から拡張子を除いた部分。|  
|$SharePoint.Feature.DeploymentPath$|パッケージ内のフィーチャーを格納しているフォルダーの名前。  このトークンは、フィーチャー デザイナーの \[配置パス\] プロパティと同じです。  値の一例を挙げると、"Project1\_Feature1" です。|  
|$SharePoint.Feature.Id$|格納しているフィーチャーの SharePoint ID。  すべてのフィーチャー レベル トークンと同様に、このトークンには、フィーチャーを介してパッケージに格納されているファイルからのみ使用できます。フィーチャーを使わずに直接パッケージに追加することはできません。|  
|$SharePoint.ProjectItem.Name$|**ISharePointProjectItem.Name** から取得した、プロジェクト項目の名前 \(ファイル名ではありません\)。|  
|$SharePoint.Type.GUID.AssemblyQualifiedName$\<\>|トークンの [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] と一致する型の完全修飾名。  [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 形式は小文字は Guid.ToString \(「D」\) の形式 \(xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\) に対応します。|  
|$SharePoint.Type.GUID.FullName$\<\>|トークン内の GUID と一致する型の完全名。  GUID には小文字が使用され、その形式は Guid.ToString\("D"\) の形式 \(xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\) に対応します。|  
  
## トークン置換ファイル拡張子リストに対する拡張子の追加  
 理論上、トークンは、パッケージ内の SharePoint プロジェクト項目に属しているすべてのファイルで使用できます。ただし、既定では、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、パッケージ ファイル、マニフェスト ファイル、および次の拡張子を持つファイルのみでトークンを検索します。  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 これらの拡張機能は、… \\program\<\>files\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools フォルダーにある Microsoft.VisualStudio.SharePoint.targets ファイルの `<TokenReplacementFileExtensions>` 要素によって定義されます。  
  
 ただし、このリストには、他のファイル拡張子を追加することができます。  これを行うには、SharePoint のターゲット ファイルのインポート\> の前に定義されている SharePoint プロジェクトの \<すべてのファイルに `<TokenReplacementFileExtensions>` PropertyGroup 要素を追加します。  
  
> [!NOTE]  
>  トークンの置換はプロジェクトのコンパイル後に発生するため、コンパイル対象のファイルの種類のファイル拡張子 \(.cs、.vb、.resx など\) は追加しないでください。  トークンはコンパイルされていないファイルでのみ置換されます。  
  
 たとえば、トークン置換ファイル名拡張子のリストに ".myextension" および ".yourextension" というファイル名の拡張子を追加するには、次の内容を .csproj ファイルに追加します。  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 また、拡張子を直接 .targets ファイルに追加する方法もあります。  ただし、この方法では、対象の SharePoint プロジェクトだけではなく、ローカル システム上でパッケージ化されるすべての SharePoint プロジェクトについて、拡張子リストが変更されます。  そのシステムを 1 人の開発者がもっぱら使用する場合や、プロジェクトの大半で同じ要件が適用される場合には便利な方法です。  ただし、変更内容がそのシステムに限定されるため、汎用性は高くありません。したがって、拡張子はプロジェクト ファイルに追加することをお勧めします。  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  