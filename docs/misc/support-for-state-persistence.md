---
title: "状態の永続性のサポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "状態の永続性、Managed Package Framework のサポート"
  - "Managed Package Framework、状態の永続性のサポート"
  - "状態、永続性"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# 状態の永続性のサポート
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は共通のオブジェクトの状態を維持できます。  たとえばソリューション プロパティおよびプロジェクト プロパティはに格納されソリューション ファイルとプロジェクト ファイルから復元されます。  ユーザー設定のエクスポートに設定ファイルからインポートできます。  
  
 VSPackage は現在のユーザーのシステム レジストリまたはアプリケーション データ フォルダーのローカル ストレージに通常コンピューターとします。  ストレージに空間を整数や文字列など必要とする値は通常システム レジストリに保存されます。  ストレージの空間の多くはビットマップなど必要とする値はファイルに格納されます。  ファイルのパス自体はシステム レジストリに保存できます。  持続機構はローカル ストレージのアクセス許可が必要です。  
  
## ローカル ストレージを検索するためのサポート  
 <xref:Microsoft.VisualStudio.Shell.Package> のクラスは現在のユーザーまたはコンピューターのシステム レジストリまたはアプリケーション データ フォルダーの状態情報を見つけることができます。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 ローカル コンピューターのレジストリ パスをルートします [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のたとえばHKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 8.0Exp を返します。  
  
 ローカルのレジストリ ルートが <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> サービスから派生します。  これができない場合はVSPackage の <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> の属性から派生します。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 現在のユーザーのコンピューターごとに \(\) のレジストリ パスをルートします [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のたとえばHKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ 8.0Exp を返します。  
  
 ローカルのレジストリ ルートが <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> サービスから派生します。  これができない場合はVSPackage の DefaultLocalRegistryRoot の属性から派生します。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 現在のローミング ユーザーの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデータ \(たとえばC:\\Documents and Settings\\*YourAccountName*\\ Application Data \\ Microsoft \\ VisualStudio \\ 8.0Exp に共通するリポジトリの役割をするディレクトリのパスを返します。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 現在の非ローミング ユーザーの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデータ \(たとえばC:\\Documents and Settings\\*YourAccountName*\\ ローカルに共通するリポジトリとして Settings \\ Application Data \\ Microsoft \\ VisualStudio \\ 8.0Exp 実行するディレクトリのパスを返します。  
  
## 参照  
 [Visual Studio の状態](/visual-cpp/misc/vspackage-state)