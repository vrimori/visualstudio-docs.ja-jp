---
title: "コマンドのデザイン | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンド"
  - "コマンドの実装"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# コマンドのデザイン
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage にコマンドを追加すると使用できるどのように処理する必要があるときに表示されます。である場所を指定する必要があります。  
  
## コマンドの定義  
 新しいコマンドを定義するにはVSPackage のプロジェクトに Visual Studio コマンドのテーブル \(.vsct\) ファイルを追加します。  Visual Studio パッケージ テンプレートによって VSPackage を作成した場合プロジェクトは次の 1 つが含まれます。  詳細については、「[Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
 Visual Studio はコマンドを表示できるようにあるすべての .vsct ファイルをマージします。  これらのファイルはVSPackage の個々のバイナリであるためVisual Studio のを検索するためにパッケージを読み込む必要はありません。  詳細については、「[Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)」を参照してください。  
  
 Visual Studio でメニュー リソースとコマンドを定義するには <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> レジスタの属性を使用します。  詳細については、「[実装](../../extensibility/internals/command-implementation.md)」を参照してください。  
  
 コマンドはいくつかの方法で実行時に変更できます。  で表示または非表示にするか有効または無効にできます。  は異なるテキストまたはアイコンを表示できます。または別の値を指定します。  大量のカスタマイズはVisual Studio が VSPackage を読み込む前に発生することがあります。  詳細については、「[Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)」を参照してください。  
  
## コマンド ハンドラー  
 コマンドを作成するとコマンドを実行するイベント ハンドラーを指定する必要があります。  ユーザーがコマンドを選択すると適切にルーティングする必要があります。  コマンドをルーティングするとユーザーがそのために有効または非表示を有効または無効にするには表示する正しい VSPackage に送信することを意味し実行します。  詳細については、「[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)」を参照してください。  
  
## Visual Studio コマンドの環境  
 Visual Studio はVSPackage の任意のホストはそれぞれ独自のコマンドのセットを提供できます。  環境が現在のタスクに適したコマンドのみが表示されます。  詳細については、「[可用性](../../extensibility/internals/command-availability.md)」および「[コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)」を参照してください。  
  
 新しいコマンドを定義する VSPackageメニューツール バーショートカット メニューがレジストリ エントリを通じてインストール時に Visual Studio のコマンド情報はネイティブ コードマネージ アセンブリのリソースを参照する示します。  各リソースはVisual Studio コマンドのテーブル \(.vsct\) ファイルをコンパイルするときに生成されるデータのバイナリ リソース \(.cto\) ファイルを参照します。  これはインストールされる VSPackage の読み込みにマージされたコマンドのセットをメニューやツール バーを使用するとVisual Studio ができます。  
  
### コマンドの整理  
 環境はグループ優先度メニューからコマンドを配置します。  
  
-   グループは関連するコマンドなど **切り取り  コピー**  と  **貼り付け**  のコマンド グループの論理的な集まりです。  グループがメニューに表示されるコマンドです。  
  
-   優先順位はグループの各コマンドがメニューに表示される順序が決まります。  
  
-   メニューがグループのコンテナーとして機能します。  
  
 環境はメニュー コマンドおよびグループを定義します。  詳細については、「[既定のコマンド、グループ、およびツールバーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)」を参照してください。  
  
 コマンドはプライマリ グループに割り当てることができます。  プライマリ グループはメイン メニューの構造体と ENT0ENT \[出力\] ダイアログ ボックスのコマンドの位置を制御します。  コマンドは複数のグループに表示できる ; たとえばメイン メニューショートカット メニューおよびツール バーです。  詳細については、「[Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)」を参照してください。  
  
### コマンド ルーティング  
 VSPackage のコマンドを呼び出すオブジェクト インスタンスのメソッドのプロセスとルーティングするプロセスは異なります。  
  
 順次環境のルートのコマンド現在の選択に基づいてする外側の \(グローバル\) コンテキストへの最も内側 \(ローカル\) コマンドのコンテキストで。  最初のコマンドを実行コンテキストがそれを処理します。  詳細については、「[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)」を参照してください。  
  
 ほとんどのインスタンスで<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを使用して環境を処理するコマンド。  コマンド ルーティングの設定がハンドルのコマンドに複数のオブジェクトに対応しているため<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> はオブジェクトのいくつでも実行できます。; これらはMicrosoft ActiveX コントロールウィンドウのビューの実装ドキュメント オブジェクトプロジェクト階層を含む VSPackage はそのコマンドについて説明します \(グローバルの場合\)。  に特化された場合たとえばルーティングは階層でコマンド <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> のインターフェイスを実装する必要があります。  
  
## 関連トピック  
  
|Title|Description|  
|-----------|-----------------|  
|[実装](../../extensibility/internals/command-implementation.md)|VSPackage のコマンドを実装する方法について説明します。|  
|[可用性](../../extensibility/internals/command-availability.md)|必要なコマンドが使用できる場合Visual Studio のコンテキストが決定する方法について説明します。|  
|[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio コマンド ルーティングのアーキテクチャはVSPackage で処理されるコマンドを有効にする方法について説明します。|  
|[配置ガイドライン](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio 環境のコマンドを配置する方法を示します。|  
|[Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackage が推奨 Visual Studio のコマンド アーキテクチャを使用する方法について説明します。|  
|[既定のコマンド、グループ、およびツールバーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|VSPackage が最適な使用法 Visual Studio に含まれているコマンド方法を説明します。|  
|[Vspackage を管理します。](../../extensibility/managing-vspackages.md)|Visual Studio によって VSPackage を読み込む方法について説明します。|  
|[Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|VSPackage でコマンドのレイアウトと外観を記述するための XML ベースの .vsct ファイルに関する情報を提供します。|