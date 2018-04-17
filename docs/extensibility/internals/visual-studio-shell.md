---
title: Visual Studio シェル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71b624cee0e55f95f90a86eac943828bbc26ac97
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェルは、プライマリのエージェントでの統合の[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 シェルでは、一般的なサービスを共有する Vspackage を有効にするために必要な機能を提供します。 のアーキテクチャの目標[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Vspackage で主要な機能を権利発生権利には、シェルは、基本的な機能を提供し、Vspackage のコンポーネント間の相互通信をサポートするためのフレームワークです。  
  
## <a name="shell-responsibilities"></a>シェルの責任  
 シェルには、次のキーの責任があります。  
  
-   ユーザー インターフェイス (UI) の基本的な要素を (を介して COM インターフェイス) をサポートします。 既定のメニューとツールバー、ドキュメント ウィンドウ フレームまたはマルチ ドキュメント インターフェイス (MDI) 子ウィンドウ、およびツール ウィンドウのフレームおよびドッキングをサポートが含まれます。  
  
-   ドキュメントの永続化を調整するために、複数の方法で、または互換性のない方法で、その 1 つのドキュメントを開くことができませんを保証するためには、実行中のドキュメント テーブル (RDT) 内のすべての現在開いているドキュメントの実行中のリストを保持します。  
  
-   コマンド ルーティングとコマンドの処理のインターフェイスをサポートする`IOleCommandTarget`です。  
  
-   適切なときに Vspackage を読み込んでいます。 遅延読み込み、VSPackage は、シェルのパフォーマンスを向上させる必要があります。  
  
-   特定の管理の共有など、サービス<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>、基本シェルの機能を提供し、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>、基本の windowing 機能を提供します。  
  
-   ソリューション (.sln) ファイルを管理します。 ソリューションには、Visual C 6.0 でのワークスペース (.dsw) ファイルと同様に、関連するプロジェクトのグループが含まれます。  
  
-   シェルの選択の追跡、コンテキスト、および通貨です。 シェルは、次の種類の項目を追跡します。  
  
    -   現在のプロジェクト  
  
    -   現在のプロジェクト アイテムまたは ItemID 現在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   現在の選択、**プロパティ**ウィンドウまたは `SelectionContainer`  
  
    -   UI コンテキスト Id または CmdUIGuids コマンド、メニューのおよびツールバーの表示を制御します。  
  
    -   アクティブなウィンドウ、ドキュメント、および元に戻すマネージャーなどの現在アクティブな要素  
  
    -   ドライブのダイナミック ヘルプのユーザー コンテキストの属性  
  
 シェルもインストールされている Vspackage と現在のサービス間の通信を仲介します。 シェルの主要な機能をサポートしに統合されているすべての VSPackages に利用できるように[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 これらのコア機能には、次の項目があります。  
  
-   **に関する** ダイアログ ボックスやスプラッシュ スクリーン  
  
-   **新規および既存項目の追加追加** ダイアログ ボックス  
  
-   **クラス ビュー**ウィンドウと**オブジェクト ブラウザー**  
  
-   **参照** ダイアログ ボックス  
  
-   **ドキュメント アウトライン**ウィンドウ  
  
-   **ダイナミック ヘルプ**ウィンドウ  
  
-   **検索**と**置き換えます**  
  
-   **プロジェクトを開く**と**ファイルを開く** ダイアログ ボックス、**新規**メニュー  
  
-   **オプション** ダイアログ ボックスで、**ツール**メニュー  
  
-   **プロパティ**ウィンドウ  
  
-   **ソリューション エクスプローラー**  
  
-   **タスク一覧**ウィンドウ  
  
-   **ツールボックス**  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackage](../../extensibility/internals/vspackages.md)