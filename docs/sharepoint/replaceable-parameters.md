---
title: 置き換え可能パラメーター |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86d6b08d209703f73901d7a839c731e1a9a63fdd
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="replaceable-parameters"></a>置き換え可能パラメーター
  置き換え可能パラメーターは、または*トークン*、プロジェクト ファイル内の実際の値は、デザイン時に認識されていない SharePoint ソリューションのアイテムの値を提供するのに使用できます。 標準には、関数に似ている[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]テンプレート トークンです。 詳細については、次を参照してください。[テンプレート パラメーター](/visualstudio/ide/template-parameters)です。  
  
## <a name="token-format"></a>トークンの形式  
 トークンの先頭し、末尾にドル記号 ($) 文字を使用します。 展開で使用されるすべてのトークンはプロジェクトが SharePoint ソリューション パッケージ (.wsp ファイル) にパッケージ化するときに実際の値に置き換えられます。 たとえば、トークン **$SharePoint.Package.Name$** 「SharePoint パッケージのテスト」です文字列に解決される可能性があります。  
  
## <a name="token-rules"></a>トークンの規則  
 トークンに、次の規則が適用されます。  
  
-   トークンは、行内の任意の場所で指定できます。  
  
-   トークンは、複数行にまたがることはできません。  
  
-   同じファイルの同じ行に、同じトークンを複数回指定することがあります。  
  
-   同じ行では、さまざまなトークンを指定します。  
  
 これらの規則に従っていないトークンは、警告やエラーを指定せずに無視されます。  
  
 文字列値を使用してトークンの置換は、マニフェストの変換後すぐに行われます。 この置き換えは、トークンをマニフェスト テンプレートを編集できます。  
  
### <a name="token-name-resolution"></a>トークン名の解決  
 ほとんどの場合は、トークンが含まれる場所に関係なく、特定の値に解決されます。 ただし、パッケージまたは機能には、トークンが関連付けられている場合、トークンの値によって異なりますが含まれています。 たとえば、機能とは場合は、パッケージ、トークン`$SharePoint.Package.Name$`「パッケージ A.」の値に解決 かどうか、同じ機能がパッケージ B、し`$SharePoint.Package.Name$`「パッケージ b.」に解決されます  
  
## <a name="tokens-list"></a>トークンの一覧  
 次の表には、使用可能なトークンが一覧表示します。  
  
|名前|説明|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|"NewProj.csproj"などを含むプロジェクト ファイルの名前です。|  
|$SharePoint.Project.FileNameWithoutExtension$|ファイル名拡張子を除いたを含むプロジェクト ファイルの名前。 たとえば、"NewProj"です。|  
|$SharePoint.Project.AssemblyFullName$|含まれるプロジェクトの表示名 (厳密な名前) には、アセンブリを出力します。|  
|$SharePoint.Project.AssemblyFileName$|アセンブリの出力を含むプロジェクトの名前。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|ファイル名拡張子の付かない、アセンブリの出力を含むプロジェクトの名前。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|含まれるプロジェクトの公開キー トークンの文字列に変換、アセンブリを出力します。 (16 文字"x2"16 進数形式です)。|  
|$SharePoint.Package.Name$|含まれるパッケージの名前。|  
|$SharePoint.Package.FileName$|含むパッケージの定義ファイルの名前。|  
|$SharePoint.Package.FileNameWithoutExtension$|(拡張子なし) を含むパッケージの定義ファイルの名前です。|  
|$SharePoint.Package.Id$|含まれるパッケージの SharePoint ID。 機能は、1 つ以上のパッケージで使用される、この値は変更されます。|  
|$SharePoint.Feature.FileName$|Feature1.feature など、含まれている機能の定義ファイルの名前。|  
|$SharePoint.Feature.FileNameWithoutExtension$|ファイル名拡張子を除いたのフィーチャー定義ファイルの名前。|  
|$SharePoint.Feature.DeploymentPath$|パッケージ内のフィーチャーが含まれているフォルダーの名前。 このトークンは、フィーチャー デザイナーで、「配置パス」プロパティに相当します。 値の例は、"Project1_Feature1"です。|  
|$SharePoint.Feature.Id$|含まれている機能の SharePoint ID。 このトークンは、as、機能を使用してパッケージに含まれるファイルだけですべての機能レベル トークンを使用していないに直接追加機能の外部でパッケージ。|  
|$SharePoint.ProjectItem.Name$|プロジェクト項目の名前のファイル名ではなくから取得した**ISharePointProjectItem.Name**です。|  
|$SharePoint.Type です。\<GUID > です。AssemblyQualifiedName $|一致する型のアセンブリ修飾名、[!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]トークンのです。 形式、[!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]は小文字と Guid.ToString("D") 形式に対応する (つまり、xxxxxxxx xxxx-xxxx-。)。|  
|$SharePoint.Type です。\<GUID > です。FullName $|トークン内の GUID と一致する型の完全名。 GUID の形式は小文字と Guid.ToString("D") 形式に対応する (つまり、xxxxxxxx xxxx-xxxx-。)。|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>トークンの置換に拡張機能を追加するファイル拡張子リスト  
 トークンは既定では、パッケージに含まれている項目を SharePoint プロジェクトに属しているすべてのファイルでは理論的に使用できますが[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]トークンでは、パッケージ ファイル、マニフェスト ファイル、および次の拡張子を持つファイルのみを検索します。  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Web パーツ  
  
-   DWP  
  
 これらの拡張機能がによって定義された、 `<TokenReplacementFileExtensions>` Microsoft.VisualStudio.SharePoint.targets ファイル内の要素にある、.\\< プログラム ファイル\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools フォルダーです。  
  
 ただし、一覧に追加のファイル拡張子を追加できます。 追加、`<TokenReplacementFileExtensions>`する前に定義されている SharePoint プロジェクト ファイル内の任意の PropertyGroup 要素、\<インポート > SharePoint ターゲット ファイルのです。  
  
> [!NOTE]  
>  トークンの置換は、プロジェクトをコンパイルした後に発生するためには、コンパイルされるファイルの種類は、.cs、.vb、.resx などのファイル拡張子を追加しないでください。 コンパイルされていないファイルだけには、トークンが置き換えられます。  
  
 たとえば、トークンの置換後のファイル名拡張子の一覧に、ファイル名拡張子".myextension"と".yourextension"を追加するには追加する、次のように、`.csproj`ファイル。  
  
```xml  
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
  
 .Targets ファイルに直接、拡張機能を追加することができます。 ただし、これを変更するだけでなく、ローカル システムでパッケージ化されたすべての SharePoint プロジェクトの拡張機能の一覧、独自です。 システム上の唯一の開発者の場合、またはほとんどのプロジェクトの必要な場合に便利ですがあります。 ただし、システムに固有である、この方法は非常に移植性ではありませんのでをお勧めするため追加するすべての拡張機能プロジェクト ファイルを代わりにします。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  