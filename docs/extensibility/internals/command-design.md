---
title: コマンドのデザイン |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 43b83e5a02fb84ad09531f87b3120168bad0b2e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132176"
---
# <a name="command-design"></a>コマンドのデザイン
VSPackage にコマンドを追加するときに表示されることが、使用可能な場合、および処理するのにはどのようにを指定する必要があります。  
  
## <a name="defining-commands"></a>コマンドを定義します。  
 新しいコマンドを定義するのには、VSPackage プロジェクトで Visual Studio コマンド テーブル (.vsct) ファイルを含めます。 Visual Studio パッケージ テンプレートを使用して、VSPackage を作成した場合、プロジェクトには、これらのファイルのいずれかが含まれます。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)です。  
  
 Visual Studio では、コマンドを表示できるように検出されたすべての .vsct ファイルをマージします。 これらのファイルはバイナリの VSPackage から区別されるため、Visual Studio は、コマンドを検索するパッケージを読み込むにはありません。 詳細については、次を参照してください。[方法 VSPackages に追加のユーザー インターフェイス要素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)です。  
  
 Visual Studio を使用して、<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>メニュー リソースとコマンドを定義する属性を登録します。 詳細については、次を参照してください。[実装](../../extensibility/internals/command-implementation.md)です。  
  
 コマンドは、実行時に、いくつかの方法で変更できます。 表示または非表示に、有効にしたりできます無効になっています。 別のテキストまたはアイコンを表示したり、別の値が含まれていることができます。 Visual Studio には、VSPackage が読み込まれる前に、さまざまなカスタマイズを実行できます。 詳細については、次を参照してください。[方法 VSPackages に追加のユーザー インターフェイス要素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)です。  
  
## <a name="command-handlers"></a>コマンド ハンドラー  
 コマンドを作成する場合は、コマンドを実行するイベント ハンドラーを指定する必要があります。 ユーザーは、コマンドを選択する場合にする必要があります適切にルーティングされます。 コマンド ルーティングを有効にする、または無効にすること、非表示またはそれを表示、そのためには、ユーザーが選択した場合は、それを実行する正しい VSPackage に送信することを意味します。 詳細については、次を参照してください。[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)です。  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio コマンド環境  
 Visual Studio には、Vspackage の任意の数をホストし、それぞれ独自のコマンド セットを行うことができます。 環境では、現在のタスクに適切なコマンドのみを表示します。 詳細については、次を参照してください。[可用性](../../extensibility/internals/command-availability.md)と[コンテキスト オブジェクトは選択](../../extensibility/internals/selection-context-objects.md)です。  
  
 新しいコマンド、メニューのツールバー、またはショートカット メニューを定義する VSPackage は、ネイティブまたはマネージ アセンブリ内のリソースを参照しているレジストリ エントリで、インストール時に、Visual Studio にそのコマンドの情報を提供します。 各リソースは、Visual Studio コマンド テーブル (.vsct) ファイルをコンパイルするときに生成される、バイナリ データのリソース (.cto) ファイルを参照します。 これにより、Visual Studio でのマージされたコマンドが設定、メニューのおよびツールバーをすべてインストールされている VSPackage を読み込むことがなく提供できます。  
  
### <a name="command-organization"></a>コマンド組織  
 環境では、グループ、優先度、およびメニューで、コマンドを配置します。  
  
-   グループは、関連するコマンドの論理的な集まり、たとえば、**切り取り**、**コピー**、および**貼り付け**コマンド グループ。 グループは、メニューに表示されるコマンドです。  
  
-   優先順位では、グループ内の個々 のコマンドがメニューに表示される順序を決定します。  
  
-   メニューは、グループのコンテナーとして機能します。  
  
 環境では、いくつかのコマンド、グループ、およびメニューは組み込まれています。 詳細については、次を参照してください。[コマンドの既定の、グループ、およびツールバー配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)です。  
  
 コマンドは、プライマリ グループに割り当てることができます。 プライマリ グループは、メインのメニュー構造と、コマンドの位置を制御、**カスタマイズ** ダイアログ ボックス。 コマンドが複数のグループに表示できます。たとえば、コマンドには、メイン メニューのショートカット メニューおよびツールバーができます。 詳細については、次を参照してください。[方法 VSPackages に追加のユーザー インターフェイス要素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)です。  
  
### <a name="command-routing"></a>コマンド ルーティング  
 呼び出すと、Vspackage のコマンドをルーティングの手順は、オブジェクトのインスタンス上のメソッドを呼び出すプロセスによって異なります。  
  
 環境では、最も外側の (グローバル) のコンテキストに現在の選択内容に基づいて、最も内側の (ローカル) コマンド コンテキストから順番にコマンドをルーティングします。 コマンドを実行することが最初のコンテキストはそれを処理します。 詳細については、次を参照してください。[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)です。  
  
 ほとんどの場合、環境処理するコマンドを使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。 コマンド ルーティング スキームにより、多数の異なるオブジェクトのコマンドを処理するため<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>任意の数のオブジェクトによって実装されることができますこれらは、Microsoft ActiveX コントロール、ウィンドウのビューの実装、ドキュメント オブジェクト、プロジェクト階層では、。VSPackage 用とオブジェクト自体 (グローバル コマンド)。 特殊な場合によっては、階層では、たとえば、コマンドをルーティング、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイスを実装する必要があります。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[実装](../../extensibility/internals/command-implementation.md)|VSPackage にコマンドを実装する方法について説明します。|  
|[可用性](../../extensibility/internals/command-availability.md)|Visual Studio のコンテキストがコマンドを使用できるを決定する方法について説明します。|  
|[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio のコマンド ルーティングのアーキテクチャが異なる Vspackage によって処理されるコマンドを利用する方法について説明します。|  
|[配置ガイドライン](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio 環境でコマンドを配置する方法を提案します。|  
|[VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Vspackage によって Visual Studio コマンドのアーキテクチャが最適なように利用する方法について説明します。|  
|[既定のコマンド、グループ、およびツール バーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Vspackage によって Visual Studio に含まれているコマンドが最適なように使用する方法について説明します。|  
|[VSPackage の管理](../../extensibility/managing-vspackages.md)|Visual Studio が Vspackage を読み込む方法について説明します。|  
|[Visual Studio Command Table (.Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|レイアウトと外観を Vspackage にコマンドの記述に使用される XML ベースの .vsct ファイルに関する情報を提供します。|