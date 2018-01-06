---
title: "SharePoint でサポートされている MSBuild プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, MSBuild properties
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: af70078790c684ce774a203b265d7c767779ab15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint でサポートされている MSBuild プロパティ
  どの[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft.VisualStudio.SharePoint.targets ファイル、プロジェクト ファイルまたはプロジェクト ユーザー ファイルで定義されているプロパティを使用することができます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint プロジェクト。 一般的なだけでなく[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]プロジェクトでは、SharePoint によって提供されるプロパティは、SharePoint プロジェクトに固有の追加のプロパティを定義します。  
  
 共通の一覧については[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]プロパティを参照してください[MSBuild プロジェクトの共通プロパティ](http://go.microsoft.com/fwlink/?LinkID=168687)です。 使用するプログラミング言語でサポートされるプロパティの一覧については、.targets ファイル、プロジェクト ファイル (.csproj または .vbproj)、またはプロジェクト ユーザー ファイルの参照 (csproj.user または。 vbproj.user)。  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint 固有の MSBuild プロパティ  
 次の表にリスト[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]の SharePoint プロジェクトに適用されるプロパティ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 その他のプロパティが存在するが、内部で使用できます。  
  
|プロパティ名|説明|  
|-------------------|-----------------|  
|SharePointSiteUrl|表す文字列、 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint サイトにします。|  
|SandboxedSolution|ソリューションがサンド ボックス ソリューションであるかどうかを示すブール値。|  
|ActiveDeploymentConfiguration|アクティブな配置構成。|  
|IncludeAssemblyInPackage|パッケージ ファイルにアセンブリが含まれるかどうかを示すブール値。|  
|PreDeploymentCommand|配置前コマンドのステップで実行するコマンドを表す文字列値。|  
|PostDeploymentCommand|配置後コマンド ステップで実行するコマンドを表す文字列値。|  
|CustomBeforeSharePointTargets|パスを表す文字列、[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]ターゲット ファイル。 ターゲット ファイルが存在するが定義されている場合、SharePoint ターゲット データの前にインポートされます。 このプロパティを使用して、付属の SharePoint のターゲット ファイルを変更しなくてもパッケージ関連のプロパティを事前に定義して、パッケージのプロセスをカスタマイズできます。 ただしターゲット ファイルがまだすべての SharePoint プロジェクトに適用できます。|  
|CustomAfterSharePointTargets|パスを表す文字列、[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]ターゲット ファイル。 ターゲット ファイルが存在するが定義されている場合、ターゲットの SharePoint データのすべてのインポートはありません。 このプロパティを使用して、付属の SharePoint のターゲット ファイルを変更しなくてもパッケージ関連のプロパティとターゲットをオーバーライドすることで、パッケージのプロセスをカスタマイズできます。 ただしターゲット ファイルがまだすべての SharePoint プロジェクトに適用できます。|  
|LayoutPath|各パッケージ化するファイルの一時的に置かれる .wsp ファイルに追加される前に、のルート ディレクトリを表す文字列。 このパスを追加、削除、または使用して、.wsp ファイルの内容を変更するためにパッケージ化するファイルを変更する BeforeLayout および AfterLayout のターゲットをオーバーライドする際に知っておくことができます。|  
|BasePackagePath|パッケージが置かれているフォルダーを表す文字列。 この値は bin \debug など、プロジェクトの出力ディレクトリを使用します。|  
|PackageExtension|パッケージに追加するファイル名拡張子を表す文字列。 既定値は、wsp です。|  
|AssemblyDeploymentTarget|SharePoint サーバー上のプロジェクト アセンブリの展開先の場所を表す文字列。 値は GlobalAssemblyCache (既定) または web アプリケーションのいずれかです。 このプロパティは、[プロパティ] ウィンドウでも設定できます。|  
|PackageWithValidation|パッケージ化する前に検証を実行するかどうかを指定するブール値。 このプロパティを使用して、パッケージのビルド時に検証エラーを無視できます。|  
|ValidatePackageDependsOn|ValidatePackage ターゲットの前に実行するその他のターゲットを定義する文字列。|  
|TokenReplacementFileExensions|パッケージ化中に置き換えられて、トークンを持つファイルを定義する文字列。|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>MSBuild プロパティを使用して、[プロパティ] ページ  
 ハードコーディングされた文字列を使用する代わりに、柔軟性、**配置前コマンドライン**と**配置後コマンドライン**ボックス SharePoint プロパティ ページで、SharePoint を使用することができます引数としてプロパティです。 特定を指定する代わりに、たとえば、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]文字列、SharePoint サイトを代わりに使用できます`$(SharePointSiteUrl)`です。  
  
> [!NOTE]  
>  使用するか、[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]の変数構文`$(` *propertyName* `)`または環境変数の構文`%` *propertyName* `%`プロパティを指定します。  
  
## <a name="see-also"></a>参照  
 [MSBuild リファレンス](/visualstudio/msbuild/msbuild-reference)  
  
  