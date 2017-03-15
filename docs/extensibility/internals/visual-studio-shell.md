---
title: "Visual Studio Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio シェル"
  - "Visual Studio シェル"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Visual Studio Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] シェルでの統合の主なエージェントは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 シェルでは、一般的なサービスを共有する VSPackages を可能にするために必要な機能を提供します。 のアーキテクチャの目的は、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、Vspackage で主要な機能を権利発生権利には、シェルは、基本的な機能を提供し、Vspackage のコンポーネント間の相互通信をサポートするためのフレームワークです。  
  
## シェルの責任  
 シェルでは、次の重要な役割があります。  
  
-   ユーザー インターフェイス \(UI\) の基本要素 \(COM インターフェイス\) をサポートします。 既定のメニューとツールバー、ドキュメント ウィンドウのフレームまたはマルチ ドキュメント インターフェイス \(MDI\) 子ウィンドウ、およびツール ウィンドウのフレームおよびドッキングをサポートが含まれます。  
  
-   ドキュメントの持続性を調整するために、複数の方法で、または互換性のない方法で、その 1 つのドキュメントを開くことができないを保証するためには、実行中のドキュメント テーブル \(RDT\) 内のすべての現在開いているドキュメントの実行中のリストを維持します。  
  
-   コマンド ルーティングとコマンド処理のインターフェイスをサポートする `IOleCommandTarget`です。  
  
-   適切なときに Vspackage を読み込んでいます。 VSPackage を遅延読み込みは、シェルのパフォーマンスを向上させる必要があります。  
  
-   特定の管理の共有など、サービス <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, 、基本シェル機能を提供し、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, 、基本的なウィンドウ処理機能を提供します。  
  
-   ソリューション \(.sln\) ファイルを管理します。 ソリューションには、Visual C 6.0 のワークスペース \(.dsw\) ファイルと同様、関連するプロジェクトのグループが含まれます。  
  
-   追跡シェル全体の選択、コンテキスト、および通貨です。 シェルでは、次の種類の項目を追跡します。  
  
    -   現在のプロジェクト  
  
    -   現在のプロジェクト項目または現在のアイテム Id <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   現在の選択、 **プロパティ** ウィンドウまたは `SelectionContainer`  
  
    -   UI のコンテキスト Id または CmdUIGuids コマンド、メニューのおよびツールバーの表示を制御します。  
  
    -   アクティブなウィンドウ、ドキュメント、および元に戻すマネージャーなどの現在アクティブな要素  
  
    -   \[ダイナミック ヘルプを促進するユーザー コンテキストの属性  
  
 シェルでは、インストールされている Vspackage と現在のサービス間の通信を仲介します。 シェルのコア機能をサポートしに統合されているすべての VSPackages に利用できるように [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 その中核となる機能は、次の項目を示します。  
  
-   **に関する** \] ダイアログ ボックスやスプラッシュ画面  
  
-   **新しいを追加し、\[既存項目の追加** ダイアログ ボックス  
  
-   **クラス ビュー** ウィンドウと **オブジェクト ブラウザー**  
  
-   **参照** \] ダイアログ ボックス  
  
-   **\[ドキュメント アウトライン** ウィンドウ  
  
-   **ダイナミック ヘルプ** ウィンドウ  
  
-   **検索** と **置換**  
  
-   **プロジェクトを開く** と **ファイルを開く** のダイアログ ボックスを表示、 **新規** メニュー  
  
-   **オプション** \] ダイアログ ボックスで、 **ツール** メニュー  
  
-   **プロパティ** ウィンドウ  
  
-   **ソリューション エクスプローラー**  
  
-   **タスク一覧** ウィンドウ  
  
-   **ツールボックス**  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Vspackages にあります。](../../extensibility/internals/vspackages.md)