---
title: コマンドの設計 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fe22e67d97af7dc7b8c900dd10c301d02d8c5a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548420"
---
# <a name="command-design"></a>コマンド デザイン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コマンド デザイン](https://docs.microsoft.com/visualstudio/extensibility/internals/command-design)します。  
  
VSPackage にコマンドを追加するときに表示されるが、可能な場合とが処理されるようにする方法を指定する必要があります。  
  
## <a name="defining-commands"></a>コマンドを定義します。  
 新しいコマンドを定義するには、VSPackage プロジェクトで Visual Studio Command Table (.vsct) ファイルが含まれます。 Visual Studio パッケージ テンプレートを使用して VSPackage を作成した場合、プロジェクトには、これらのファイルのいずれかが含まれます。 詳細については、次を参照してください。 [Visual Studio Command Table (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
 Visual Studio では、コマンドを表示できるように検出されたすべての .vsct ファイルをマージします。 これらのファイルはバイナリの VSPackage から個別であるために、Visual Studio は、コマンドを検索するパッケージを読み込むにはありません。 詳細については、次を参照してください。[方法 VSPackages に追加のユーザー インターフェイス要素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)します。  
  
 Visual Studio を使用して、<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>メニュー リソースとコマンドを定義する属性を登録します。 詳細については、次を参照してください。[実装](../../extensibility/internals/command-implementation.md)します。  
  
 コマンドは、実行時に多数の異なる方法で変更できます。 ことができますを表示または非表示に、有効または無効にします。 別のテキストまたはアイコンを表示したり、異なる値を格納することができます。 Visual Studio には、VSPackage が読み込まれる前に、さまざまなカスタマイズを実行する可能性があります。 詳細については、次を参照してください。[方法 VSPackages に追加のユーザー インターフェイス要素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)します。  
  
## <a name="command-handlers"></a>コマンド ハンドラー  
 コマンドを作成するときに、コマンドを実行するイベント ハンドラーを提供する必要があります。 ユーザーは、コマンドを選択する場合にする必要があります適切にルーティングされます。 コマンドのルーティングを有効にするまたは無効にすること、非表示または表示、およびそのためには、ユーザーが選択した場合は、それを実行する正しい VSPackage に送信することを意味します。 詳細については、次を参照してください。[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)します。  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio コマンドの環境  
 Visual Studio には、Vspackage の任意の数をホストし、それぞれ独自のコマンド セットを投稿することができます。 環境では、現在のタスクに適切なコマンドのみが表示されます。 詳細については、次を参照してください。[可用性](../../extensibility/internals/command-availability.md)と[コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)します。  
  
 新しいコマンド、メニューのツールバー、またはショートカット メニューを定義する VSPackage は、ネイティブまたはマネージ アセンブリにリソースを参照するレジストリ エントリでは、インストール時、Visual Studio にそのコマンドの情報を提供します。 各リソースは、Visual Studio Command Table (.vsct) ファイルをコンパイルするときに生成されるバイナリ データ (.cto) のリソース ファイルを参照します。 これにより、Visual Studio をすべてインストールされている VSPackage を読み込むことがなくマージされたコマンド セット、メニュー、ツールバーを提供することができます。  
  
### <a name="command-organization"></a>コマンドの組織  
 環境では、グループ、優先度、メニューでコマンドを配置します。  
  
-   グループは、関連するコマンドの論理的なコレクション、たとえば、**切り取り**、**コピー**、および**貼り付け**コマンド グループ。 グループは、メニューに表示されるコマンドです。  
  
-   優先順位は、グループ内の個々 のコマンドがメニューに表示される順序を決定します。  
  
-   メニューは、グループのコンテナーとして機能します。  
  
 環境はいくつかのコマンド、グループ、およびメニューが組み込まれています。 詳細については、次を参照してください。[コマンドの既定の、グループ、およびツールバーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)します。  
  
 コマンドは、プライマリ グループに割り当てることができます。 プライマリ グループは、メインのメニュー構造とコマンドの位置を制御、**カスタマイズ** ダイアログ ボックス。 コマンドは、複数のグループに表示できます。たとえば、コマンドには、メイン メニューのショートカット メニューおよびツールバーができます。 詳細については、次を参照してください。[方法 VSPackages に追加のユーザー インターフェイス要素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)します。  
  
### <a name="command-routing"></a>コマンド ルーティング  
 呼び出すと、Vspackage 用コマンドのルーティングのプロセスは、オブジェクトのインスタンスに対してメソッドを呼び出してのプロセスによって異なります。  
  
 環境では、現在の選択に基づいて、最も内側の (ローカル) コマンド コンテキストから順番に (グローバル) の最も外側のコンテキストにコマンドをルーティングします。 コマンドを実行することが最初のコンテキストは、処理を行います。 詳細については、次を参照してください。[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)します。  
  
 ほとんどの場合、環境を使用してコマンドを処理、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。 コマンド ルーティング スキームにより、多数の異なるオブジェクトのコマンドを処理するため、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>任意の数のオブジェクトによって実装されることができますこれらは、Microsoft ActiveX コントロール、ウィンドウ ビューの実装、ドキュメント オブジェクト、プロジェクトの階層。VSPackage 用とオブジェクト自体 (グローバル コマンド)。 いくつかの特殊化された場合、階層では、たとえば、コマンドのルーティング、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイスを実装する必要があります。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[実装](../../extensibility/internals/command-implementation.md)|コマンドを VSPackage に実装する方法について説明します。|  
|[利用可能性](../../extensibility/internals/command-availability.md)|Visual Studio のコンテキストがどのコマンドは、使用を決定する方法について説明します。|  
|[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio のコマンド ルーティングのアーキテクチャが異なる Vspackage によって処理されるコマンドを使用する方法について説明します。|  
|[配置のガイドライン](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio 環境でのコマンドを配置する方法を示しています。|  
|[VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Vspackage によって Visual Studio コマンドのアーキテクチャが最もように利用する方法について説明します。|  
|[既定のコマンド、グループ、およびツール バーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Vspackage によって Visual Studio に含まれているコマンドが最適なように使用する方法について説明します。|  
|[VSPackage の管理](../../extensibility/managing-vspackages.md)|Visual Studio が Vspackage を読み込む方法について説明します。|  
|[Visual Studio Command Table (.Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|レイアウトと外観の Vspackage のコマンドの記述に使用すると、XML ベースの .vsct ファイルに関する情報を提供します。|

