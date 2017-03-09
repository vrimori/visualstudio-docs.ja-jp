---
title: "状態の永続性と Visual Studio IDE | Microsoft Docs"
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
  - "IDE 設定、状態の永続性"
  - "ユーザー設定 [Visual Studio SDK]、永続化"
  - "[ツール オプション] ページ [Visual Studio SDK]、永続化設定"
  - "IDE、状態の永続性"
  - "永続性、ユーザー設定"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 状態の永続性と Visual Studio IDE
統合開発環境 \(ENT4ENT \[入力\] メニューの **\*\*\* Import\/Export Settings \*\*\*** のコマンドは \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のカスタマイズのインポートとエクスポートします。  [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の構成 API はユーザーが **\*\*\* Import\/Export Settings \*\*\*** のコマンドを選択したときに保持する一つ以上の設定カテゴリ \(状態変数のグループ\) を定義することを VSPackage ができます。  
  
 GUID は各設定のカテゴリを指定し参照される独自の  *カスタム*  レジストリ エントリに  *塗りつぶされます点*  定義されます。  
  
> [!NOTE]
>  **ツール   オプション**  のページで **ツールボックス**  と `Microsoft.VisualStudio.Shell.DialogPage` の標準の実装は永続化に自動的にサポートされています。  構成 API は既定の動作をオーバーライドできます。  詳細については、「[ツールボックスの拡張](../misc/extending-the-toolbox.md)」、「[\[オプション\] ページ](../Topic/Options%20Pages.md)」、および「<xref:Microsoft.VisualStudio.Shell.DialogPage>」を参照してください。  
  
## このセクションの内容  
 [ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)  
 特定の VSPackage で使用される [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実装を指定するために使用されるレジストリ設定\) と点 \(指していてカスタム属性について説明します。  
  
 [方法: 相互運用機能アセンブリを使用して設定をエクスポートする](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 相互運用機能アセンブリに基づく VSPackages に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の機能を使用して保存する構成データのサポートを実装する方法の詳細な説明を提供します。  
  
 [方法: 相互運用機能アセンブリを使用して設定をインポートする](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 相互運用機能アセンブリに基づく VSPackages に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の機能を使用して構成データを取得するためのサポートを実装する方法の詳細な説明を提供します。  
  
 [設定のエクスポート](../misc/exporting-settings.md)  
 マネージ パッケージ フレームワークに基づく VSPackages に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の機能を使用して保存する構成データのサポートを実装する方法の詳細について説明します。  
  
 [設定のインポート](/visual-cpp/misc/importing-settings)  
 マネージ パッケージ フレームワークに基づく VSPackages に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の機能を使用して構成データを取得するためのサポートを実装する方法の詳細な説明を提供します。  
  
## 関連項目  
 [Working with Settings](http://msdn.microsoft.com/ja-jp/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 IDE のインポートとエクスポートのセクションを管理する方法について説明します。  
  
 [\[オプション\] ページ](../Topic/Options%20Pages.md)  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] が  **ツール**  管理のあるかまたは作成する新しい  **オプション**  のページに自動的に提供されるサポートについて説明します。  
  
 [ツールボックスの拡張](../misc/extending-the-toolbox.md)  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] が  **ツールボックス**  を管理する場合または拡張するに自動的に提供されるサポートについて説明します。  
  
 [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)  
 VSPackage を取得するためにユーザー設定を保持するようにプログラミングする方法について説明します。