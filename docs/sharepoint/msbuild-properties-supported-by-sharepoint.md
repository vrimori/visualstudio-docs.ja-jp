---
title: "SharePoint でサポートされている MSBuild プロパティ"
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
  - "Visual Studio での SharePoint 開発, MSBuild プロパティ"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# SharePoint でサポートされている MSBuild プロパティ
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトでは、Microsoft.VisualStudio.SharePoint.targets ファイル、プロジェクト ファイル、またはプロジェクト ユーザー ファイルで定義されているすべての [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] プロパティを使用できます。  SharePoint では、プロジェクトによって提供される共通の [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] プロパティのほかに、SharePoint プロジェクトに固有の追加のプロパティが定義されています。  
  
 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] の共通プロパティの一覧については、"参照してください [MSBuild プロジェクトの共通プロパティ](http://go.microsoft.com/fwlink/?LinkID=168687)。  特定のプログラミング言語でサポートされるプロパティの完全な一覧については、.targets ファイル、プロジェクト ファイル \(.csproj または .vbproj\)、またはプロジェクト ユーザー ファイル \(csproj.user または .vbproj.user\) を参照してください。  
  
## SharePoint に固有の MSBuild プロパティ  
 次の表に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint プロジェクトのみに適用される [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] プロパティを示します。  これ以外のプロパティもありますが、それらは内部で使用されるプロパティです。  
  
|プロパティ名|説明|  
|------------|--------|  
|SharePointSiteUrl|SharePoint サイトの [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] を表す文字列。|  
|SandboxedSolution|ソリューションがサンドボックス ソリューションかどうかを示すブール値。|  
|ActiveDeploymentConfiguration|アクティブな配置構成。|  
|IncludeAssemblyInPackage|アセンブリがパッケージ ファイルに含まれているかどうかを示すブール値。|  
|PreDeploymentCommand|配置前コマンド ステップで実行するコマンドを表す文字列値。|  
|PostDeploymentCommand|配置後コマンド ステップで実行するコマンドを表す文字列値。|  
|CustomBeforeSharePointTargets|[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] ターゲット ファイルのパスを表す文字列。  そのターゲット ファイルが存在し、定義されていれば、SharePoint ターゲット データの前にインポートされます。  このプロパティを使用すると、付属の SharePoint ターゲット ファイルを変更せずに、パッケージ関連のプロパティを事前に定義してパッケージ プロセスをカスタマイズできます。ただし、その場合も、SharePoint ターゲット ファイルはすべての SharePoint プロジェクトに適用されます。|  
|CustomAfterSharePointTargets|[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] ターゲット ファイルのパスを表す文字列。  そのターゲット ファイルが存在し、定義されていれば、すべての SharePoint ターゲット データの後にインポートされます。  このプロパティを使用すると、付属の SharePoint ターゲット ファイルを変更せずに、パッケージ関連のプロパティとターゲットをオーバーライドしてパッケージ プロセスをカスタマイズできます。ただし、その場合も、SharePoint ターゲット ファイルはすべての SharePoint プロジェクトに適用されます。|  
|LayoutPath|パッケージ化される各ファイルが .wsp ファイルに追加される前に一時的に配置される場所のルート ディレクトリを表す文字列。  このパスがわかると .wsp ファイルの内容を変更できるため、BeforeLayout ターゲットと AfterLayout ターゲットをオーバーライドしてパッケージ化の対象のファイルを追加、削除、または変更する場合に便利です。|  
|BasePackagePath|パッケージが配置されるフォルダーを表す文字列。  この値にはプロジェクトの出力ディレクトリ \(Bin\\Debug など\) が使用されます。|  
|PackageExtension|パッケージに追加されるファイル名拡張子を表す文字列。  既定値は wsp です。|  
|AssemblyDeploymentTarget|プロジェクト アセンブリが配置される SharePoint サーバー上の場所を表す文字列。  値は、GlobalAssemblyCache \(既定値\) または WebApplication です。  このプロパティは、プロパティ ウィンドウで設定することもできます。|  
|PackageWithValidation|パッケージ化の前に検証を実行するかどうかを示すブール値。  このプロパティを使用すると、パッケージのビルド時に検証エラーを無視できます。|  
|ValidatePackageDependsOn|ValidatePackage ターゲットの前に実行する追加のターゲットを定義する文字列。|  
|TokenReplacementFileExensions|パッケージ化の際にトークンが置き換えられるファイルを定義する文字列。|  
  
## プロパティ ページでの MSBuild プロパティの使用  
 SharePoint プロパティ ページの **\[配置前コマンド ライン\]** ボックスと **\[配置後コマンド ライン\]** ボックスでは、柔軟性を向上させるために、ハードコーディングされた文字列の代わりに引数を使用することができます。  たとえば、SharePoint サイトの特定の [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 文字列を指定する代わりに `$(SharePointSiteUrl)` を使用できます。  
  
> [!NOTE]  
>  プロパティの指定には、[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 変数の構文 \(`$(`*propertyName*`)`\) を使用することも、環境変数の構文 \(`%`*propertyName*`%`\) を使用することもできます。  
  
## 参照  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  
  
  