---
title: 置き換え可能パラメーター |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 792c7faf9ed704dd01226c750e9898965111c414
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871950"
---
# <a name="replaceable-parameters"></a>置き換え可能パラメーター
  置き換え可能パラメーター、または*トークン*、実際の値は、デザイン時にわかっていない SharePoint のソリューション項目の値を指定するプロジェクト ファイル内で使用できます。 標準の関数と似ています[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]テンプレート トークンです。 詳細については、次を参照してください。[テンプレート パラメーター](../ide/template-parameters.md)します。  
  
## <a name="token-format"></a>トークンの形式
 トークンの先頭し、ドル記号 ($) 文字で終了します。 デプロイに使用される任意のトークンが置き換え実際の値プロジェクトが SharePoint ソリューション パッケージにパッケージ化 (*.wsp*ファイル)。 たとえば、トークン **$SharePoint.Package.Name$** 「SharePoint パッケージのテスト」の文字列に解決する可能性があります。  
  
## <a name="token-rules"></a>トークンの規則
 トークンに、次の規則が適用されます。  
  
- トークンは、行の任意の場所に指定できます。  
  
- トークンは、複数行にまたがることはできません。  
  
- 同じファイルで同じ行に 2 回以上同じトークンを指定する可能性があります。  
  
- 同じ行にさまざまなトークンを指定することがあります。  
  
  これらの規則に従っていないトークンは無視され、警告またはエラーにはなりません。  
  
  文字列値を使用してトークンの置換は、マニフェストの変換の直後に実行されます。 この置換は、トークンを使用したマニフェスト テンプレートを編集できます。  
  
### <a name="token-name-resolution"></a>トークン名の解決
 ほとんどの場合は、トークンが含まれる場所に関係なく、特定の値に解決されます。 ただし、パッケージまたは機能には、トークンが関連付けられている場合、トークンの値は、含まれているに依存します。 たとえば、機能が場合は、トークンをパッケージ`$SharePoint.Package.Name$`「パッケージ A.」の値を解決します。 同じ機能がパッケージ b、かどうか`$SharePoint.Package.Name$`「パッケージ b.」に解決されます  
  
## <a name="tokens-list"></a>トークンの一覧
 次の表は、使用可能なトークンを一覧表示します。  
  
|名前|説明|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|格納先の名前のプロジェクト ファイルなど、 *NewProj.csproj*します。|  
|$SharePoint.Project.FileNameWithoutExtension$|ファイル名拡張子を除いた含むプロジェクト ファイルの名前。 たとえば、"NewProj"です。|  
|$SharePoint.Project.AssemblyFullName$|含まれるプロジェクトの表示名 (厳密な名前) には、アセンブリを出力します。|  
|$SharePoint.Project.AssemblyFileName$|アセンブリの出力に含まれるプロジェクトの名前。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|ファイル名拡張子を除いた、アセンブリの出力に含まれるプロジェクトの名前。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|含まれるプロジェクトの公開キー トークンには、文字列に変換して、アセンブリの出力です。 (16 文字"x2"16 進数形式です)。|  
|$SharePoint.Package.Name$|含まれるパッケージの名前。|  
|$SharePoint.Package.FileName$|含まれるパッケージの定義ファイルの名前。|  
|$SharePoint.Package.FileNameWithoutExtension$|含まれるパッケージの定義ファイルの名前を (拡張子なし)。|  
|$SharePoint.Package.Id$|含まれるパッケージの SharePoint ID。 1 つ以上のパッケージで機能を使用する場合は、この値が変更されます。|  
|$SharePoint.Feature.FileName$|などの定義ファイルの名前が機能*Feature1.feature*します。|  
|$SharePoint.Feature.FileNameWithoutExtension$|ファイル名拡張子を除いた、機能の定義ファイルの名前。|  
|$SharePoint.Feature.DeploymentPath$|パッケージの機能を含むフォルダーの名前。 このトークンは、フィーチャーのデザイナーで「展開パス」プロパティに相当します。 例の値は、"Project1_Feature1 です"。|  
|$SharePoint.Feature.Id$|含まれている機能の SharePoint ID。 このトークンは、ようにすべての機能レベルのトークンでは、機能を使用してパッケージに含まれるファイルでのみ使用できましていないに直接追加機能の外部のパッケージ。|  
|$SharePoint.ProjectItem.Name$|取得した (そのファイル名ではなく)、プロジェクト項目の名前**ISharePointProjectItem.Name**します。|  
|$SharePoint.Type.\<GUID>.AssemblyQualifiedName$|一致する型のアセンブリ修飾名、[!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]のトークン。 形式、[!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]は小文字と Guid.ToString("D") 形式に対応しています (つまり、xxxxxxxx xxxx-xxxx-。)。|  
|$SharePoint.Type.\<GUID>.FullName$|トークン内の GUID と一致する型の完全名。 GUID の形式は、小文字と Guid.ToString("D") 形式に対応しています (つまり、xxxxxxxx xxxx-xxxx-。)。|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>トークンの置換後のファイル拡張子の一覧に拡張機能を追加します。
 理論的には既定では、パッケージ内に、項目に含まれる SharePoint プロジェクトに属しているすべてのファイルでのトークンを使用できますが[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]パッケージ ファイル、マニフェスト ファイルは、次の拡張子を持つファイルでのみトークンを検索します。  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Web パーツ  
  
- DWP  
  
  これらの拡張機能がによって定義されている、`<TokenReplacementFileExtensions>`内にある、Microsoft.VisualStudio.SharePoint.targets ファイル内の要素、.\\< プログラム ファイル\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools フォルダー。  
  
  ただし、一覧に追加のファイル拡張子を追加することができます。 追加、`<TokenReplacementFileExtensions>`する前に定義されている SharePoint プロジェクト ファイル内の任意の PropertyGroup 要素、\<インポート > のターゲットの SharePoint ファイル。  
  
> [!NOTE]  
>  など、コンパイルされるファイルの種類のファイル拡張子を追加しないでくださいトークンの置換は、プロジェクトをコンパイルした後に発生するため、 *.cs*、 *.vb*または *.resx*します。 コンパイルされないファイルだけには、トークンが置き換えられます。  
  
 たとえば、ファイル名拡張子を追加する (*.myextension*と *.yourextension*)、トークンの置換後のファイル名拡張子の一覧には、プロジェクトには、次を追加します (*.csproj*) ファイル。  
  
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
  
 ターゲットに直接、拡張機能を追加することができます (*.targets*) ファイル。 ただし、拡張機能は、ローカル システムにパッケージ化されたすべての SharePoint プロジェクトの拡張機能の一覧を変更します。 追加すると、だけでなく、独自です。 この拡張機能は、システムの唯一の開発者の場合、または、プロジェクトの大半が必要な場合に便利な可能性があります。 ただし、システムに固有では、この方法は、ポータブルではありません、およびそのため、ことが推奨されますので、追加するすべての拡張機能プロジェクト ファイルに代わりにします。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
