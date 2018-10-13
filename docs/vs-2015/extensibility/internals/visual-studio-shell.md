---
title: Visual Studio Shell |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f0ef1e207fffc4d44963b968caad392b9d976c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222405"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]シェルは、プライマリのエージェントでの統合の[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 シェルは、一般的なサービスを共有する Vspackage を有効にするために必要な機能を提供します。 のアーキテクチャの目的は、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Vspackage では主要な機能をというには、シェルは、基本的な機能を提供し、Vspackage のコンポーネント間の相互通信をサポートするためのフレームワークです。  
  
## <a name="shell-responsibilities"></a>シェルの責任  
 シェルでは、次の主な責任があります。  
  
-   (COM インターフェイス) を通じて、ユーザー インターフェイス (UI) の基本的な要素をサポートします。 既定のメニューとツールバー、ドキュメント ウィンドウ フレームまたはマルチ ドキュメント インターフェイス (MDI) 子ウィンドウ、およびツール ウィンドウのフレームおよびドッキングのサポートが含まれます。  
  
-   ドキュメントの持続性を調整するために、および 1 つ以上の方法で、または互換性のない方法で、その 1 つのドキュメントを開くことはできませんを保証するためには、実行中、実行中のドキュメント テーブル (RDT) 内のすべての現在開いているドキュメントの一覧を維持します。  
  
-   コマンド ルーティングとコマンド処理インターフェイスをサポートしている`IOleCommandTarget`します。  
  
-   適切なタイミングで Vspackage を読み込んでいます。 VSPackage の遅延読み込みは、シェルのパフォーマンスを向上させる必要があります。  
  
-   特定の管理は共有など、サービス、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>、基本的なシェルの機能を提供して<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>、基本的なウィンドウ操作機能を提供します。  
  
-   ソリューション (.sln) ファイルを管理します。 ソリューションには、Visual C 6.0 のワークスペース (.dsw) ファイルと同様に、関連するプロジェクトのグループが含まれます。  
  
-   追跡シェル全体の選択、コンテキスト、および通貨。 シェルでは、次の種類の項目を追跡します。  
  
    -   現在のプロジェクト  
  
    -   現在のプロジェクト項目または現在の itemid であります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   現在の選択、**プロパティ**ウィンドウまたは `SelectionContainer`  
  
    -   Id または CmdUIGuids コマンド、メニューのおよびツールバーの表示を制御する UI コンテキスト  
  
    -   アクティブなウィンドウ、ドキュメント、および元に戻すマネージャーなどの現在アクティブな要素  
  
    -   ダイナミック ヘルプを促進するユーザー コンテキストの属性  
  
 シェルもインストールされている Vspackage と現在のサービス間の通信を仲介します。 シェルのコア機能をサポートしに統合されているすべての VSPackages に利用できるように[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 これらのコア機能には、次の項目があります。  
  
-   **について** ダイアログ ボックスやスプラッシュ スクリーン  
  
-   **新規および既存項目の追加を追加** ダイアログ ボックス  
  
-   **クラス ビュー**ウィンドウと**オブジェクト ブラウザー**  
  
-   **参照** ダイアログ ボックス  
  
-   **ドキュメント アウトライン**ウィンドウ  
  
-   **ダイナミック ヘルプ**ウィンドウ  
  
-   **検索**と**置き換えます**  
  
-   **プロジェクトを開く**と**ファイルを開く** ダイアログ ボックス、**新規**メニュー  
  
-   **オプション** ダイアログ ボックスで、**ツール**メニュー  
  
-   **[プロパティ]** ウィンドウ  
  
-   **ソリューション エクスプローラー**  
  
-   **タスク一覧**ウィンドウ  
  
-   **ツールボックス**  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackage](../../extensibility/internals/vspackages.md)

