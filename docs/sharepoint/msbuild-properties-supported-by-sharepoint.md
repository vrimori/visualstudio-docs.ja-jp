---
title: SharePoint でサポートされる MSBuild プロパティ |Microsoft Docs
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
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55561d570605cfd5690fc0459444b2fbadeca51a
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684809"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint でサポートされる MsBuild プロパティ
  すべて[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft.VisualStudio.SharePoint.targets ファイル、プロジェクト ファイル、またはプロジェクト ユーザー ファイルで定義されているプロパティを使用することができます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint プロジェクト。 一般的なだけでなく[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]プロパティは、プロジェクトでは、SharePoint によって提供される SharePoint プロジェクトに固有の追加のプロパティを定義します。  
  
 共通の一覧については[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]プロパティを参照してください[MSBuild プロジェクトの共通プロパティ](http://go.microsoft.com/fwlink/?LinkID=168687)します。 使用するプログラミング言語でサポートされるプロパティの完全な一覧、検索、 *.targets*ファイル、プロジェクト ファイル (*.csproj*または *.vbproj*)、またはプロジェクト ユーザー ファイル (*csproj.user*または *. vbproj.user*)。  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint に固有の MsBuild プロパティ
 次の表[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]の SharePoint プロジェクトに適用するプロパティ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 その他のプロパティが存在するが、これらは内部使用用です。  
  
|プロパティ名|説明|  
|-------------------|-----------------|  
|SharePointSiteUrl|表す文字列、 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint サイトにします。|  
|SandboxedSolution|ソリューションがサンド ボックス ソリューションであるかどうかを示すブール値。|  
|ActiveDeploymentConfiguration|アクティブな配置構成。|  
|IncludeAssemblyInPackage|パッケージ ファイルにアセンブリを含めるかどうかを示すブール値。|  
|PreDeploymentCommand|配置前コマンドのステップで実行するコマンドを表す文字列値。|  
|PostDeploymentCommand|配置後コマンドのステップで実行するコマンドを表す文字列値。|  
|CustomBeforeSharePointTargets|パスを表す文字列を[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]ターゲット ファイル。 ターゲット ファイルが存在し、定義されている場合は、SharePoint のターゲット データの前にインポートされます。 このプロパティでは、付属の SharePoint のターゲット ファイルを変更することがなくパッケージ関連のプロパティを事前に定義して、パッケージのプロセスをカスタマイズできます。 まだ、ターゲット ファイルがまだすべての SharePoint プロジェクトに適用します。|  
|CustomAfterSharePointTargets|パスを表す文字列を[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]ターゲット ファイル。 ターゲット ファイルが存在し、定義されている場合、ターゲットの SharePoint データのすべてのインポートはありません。 このプロパティでは、付属の SharePoint のターゲット ファイルを変更する必要なくパッケージ関連のプロパティとターゲットをオーバーライドすることで、パッケージのプロセスをカスタマイズできます。 まだ、ターゲット ファイルがまだすべての SharePoint プロジェクトに適用します。|  
|LayoutPath|これらのパッケージ化するファイルが一時的に配置に追加される前に、ルート ディレクトリを表す文字列、 *.wsp*ファイル。 このパスは、追加、削除、または使用しての内容を変更するためにパッケージ化するファイルを変更する BeforeLayout および AfterLayout のターゲットをオーバーライドする場合を把握するのに役立ちます、 *.wsp*ファイル。|  
|BasePackagePath|パッケージが置かれているフォルダーを表す文字列。 この値は bin \debug など、プロジェクトの出力ディレクトリを使用します。|  
|PackageExtension|パッケージに追加するファイル名拡張子を表す文字列。 既定値は、wsp です。|  
|AssemblyDeploymentTarget|SharePoint サーバー上のプロジェクト アセンブリの配置場所を表す文字列。 その値は、GlobalAssemblyCache (既定値) または web アプリケーションのいずれかです。 このプロパティは、[プロパティ] ウィンドウでも設定できます。|  
|PackageWithValidation|パッケージ化する前に検証を実行するかどうかを指定するブール値。 このプロパティを使用して、パッケージのビルド時に検証エラーを無視できます。|  
|ValidatePackageDependsOn|ValidatePackage ターゲットの前に実行する追加のターゲットを定義する文字列。|  
|TokenReplacementFileExensions|パッケージ化中に置き換え、トークンを持つファイルを定義する文字列。|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>MsBuild プロパティを使用して、[プロパティ] ページ
 ハード コーディングされた文字列を使用するのではなく、柔軟性、**配置前コマンドライン**と**配置後コマンドライン**ボックス SharePoint プロパティ ページで、SharePoint を使用することができます引数としてのプロパティです。 特定の指定ではなく、たとえば、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]文字列、SharePoint サイトの代わりに使える`$(SharePointSiteUrl)`します。  
  
> [!NOTE]  
>  いずれかを使用することができます、[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]変数構文`$(` *propertyName* `)`または環境変数の構文`%` *propertyName* `%`プロパティを指定します。  
  
## <a name="see-also"></a>関連項目

- [MSBuild リファレンス](../msbuild/msbuild-reference.md)  