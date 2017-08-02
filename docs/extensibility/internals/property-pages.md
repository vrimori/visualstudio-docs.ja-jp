---
title: "[プロパティ ページ] | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロパティを変更する構成オプション"
  - "プロパティ ページ"
  - "[プロパティ ページ] 構成オプションを変更します。"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# [プロパティ ページ]
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ユーザーがプロパティ ページを使用してプロジェクト構成に依存しないと独立したプロパティを表示および変更できます。  \[入力\] ENT0ENT ボタンの ENT1ENT \[出力\] ウィンドウに選択したオブジェクトのプロパティ ページのビューを提供するオブジェクトのソリューション エクスプローラーのツール バーで有効になります。  プロパティ ページで環境によって作成されソリューションおよびプロジェクトに対して使用できます。  がまたは構成依存プロパティを使用するプロジェクト項目で利用できるようにできます。  この機能はプロジェクト内のファイルはコンパイラ スイッチの設定が正しくビルドする必要がある場合に使用されることがあります。  
  
## プロパティ ページを使用して  
 プロパティ ページが既におよび選択の変更 \(ソリューションからプロジェクトに表示する新しい選択のプロパティを表示するにはページで表示される情報は変更します。  プロパティ ページをサポートするオブジェクトにプロパティがない場合はプロパティ ページは空です。  
  
 複数のオブジェクトを選択するとプロパティ ページで選択した項目のプロパティの積集合が表示されます。  選択した項目が構成依存プロパティを使用してソリューション エクスプローラーのツール バーの \[ENT0ENT\] ボタンをクリックするとプロパティ ウィンドウにフォーカスを移動します。  \[プロパティ\] ウィンドウと選択に関する詳細については[プロパティを拡張します。](../../extensibility/internals/extending-properties.md) を参照してください。  
  
 プロパティは複数のオブジェクトで表示およびプロパティ ページの値を変更するとオブジェクトの値はすべて新しい値が別のオブジェクトのプロパティが表示されたときに最初に異なる場合ページは空白の設定です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で使用できる  **プロジェクト**  の ENT1ENT \[出力\] ダイアログ ボックスの 2 個の一般的な種類があります。  1 番目のではVisual Basic プロジェクトの場合プロパティ ページは次のスクリーン ショットに示すようにフィールドの形式を使用して表示されます。  2 番目のではこのセクションで後述\) でもプロパティ ページがプロパティ ウィンドウに表示される場合と同様にプロパティ グリッドをホストします。  
  
 ![Visual Basic プロパティ ページ](~/docs/extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
フィールド形式およびツリー構造を使用したプロジェクトの \[プロパティ ページ\] ダイアログ ボックス  
  
 プロパティ ページ\] ダイアログ ボックスのツリー構造が <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> を使ってビルドされます。  <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> のインターフェイスによって渡されるレベル名に基づいて環境を作成します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のプロパティ ページにある 2 台のトップレベルのカテゴリがあります :  
  
-   共通プロパティは選択したオブジェクトまたはオブジェクトの構成に依存しない情報が表示されます。  そのため共通プロパティのサブカテゴリの 1 つが選択した場合ダイアログ ボックス上部の間で構成プラットフォーム構成マネージャー オプションは使用できません。  
  
-   構成プロパティソリューションまたはプロジェクトのデバッグ最適化ビルドのパラメーターに対して構成依存情報が表示されます。  
  
 追加のトップレベルのカテゴリを作成できません `IVsPropertyPage`1 の実装のいずれか一つを表示することもできます。  たとえばオブジェクトに表示する構成に依存しないプロパティが共通のプロパティのカテゴリを表示することもできます。  構成オブジェクト \(`IVsCfg``IVsProjectCfg` および関連するインターフェイスを実装するオブジェクト\) の `ISpecifyPropertyPages` を実行すると `ISpecifyPropertyPages` が項目から参照するオブジェクトおよび構成プロパティを実装する共通プロパティが表示されます。  
  
 トップレベルのカテゴリの下に表示されているカテゴリは別のプロパティ ページを表します。  ダイアログ ボックスで使用可能なカテゴリとサブカテゴリのエントリは `ISpecifyPropertyPages` と `IVsPropertyPage` の実装によって決まります。  
  
 `IDispatch` はクラス ID のリストを列挙するプロパティ ページの実装 `ISpecifyPropertyPages` に表示するプロパティを持つ選択コンテナーの項目について説明します。  `ISpecifyPropertyPages` に変数としてクラス ID が渡されプロパティ ページのインスタンスを作成するために使用されます。  クラス ID の一覧は`IVsPropertyPage` にダイアログ ボックスの左側にツリー構造を作成するために渡されます。  プロパティ ページには `IDispatch` のオブジェクトに割り当てると情報を実装する `ISpecifyPropertyPages` 渡し各ページの情報を塗りつぶします。  
  
 参照オブジェクトのプロパティが選択コンテナー内の各オブジェクトの `IDispatch` を使用して取得されます。  
  
 VSPackage の `Help::DisplayTopicFromF1Keyword` を実行するには\[ヘルプ\] ボタンの機能を提供します。  
  
 詳細についてはMSDN ライブラリの `IDispatch` と `ISpecifyPropertyPages` を参照してください。  
  
 サンプルに表示されるプロパティ ページの 2 番目の型は次のスクリーン ショットに示すようにプロパティ グリッドでフォームのホスト。  
  
 ![VC プロパティ ページ](~/docs/extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
プロパティ グリッドでプロパティ ページ\] ダイアログ ボックス  
  
 インターフェイス`IVSMDPropertyBrowser` （`IVSMDPropertyBrowser``IVSMDPropertyGrid`vsmanaged.h で宣言されている）ダイアログ ボックスまたはウィンドウ内のプロパティ グリッドを作成し設定に使用されます。  
  
 プロジェクトのアーキテクチャは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の過去のバージョンから大幅に変更されています。  特にアクティブの概念が変更されています。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ではアクティブなプロジェクトの概念はありません。  コンテキストにかかわらずコマンドを受け入れますビルドおよび配置する前の開発環境ではアクティブなプロジェクトがありました。  次にソリューションのコントロールと仲裁するすべてのプロジェクトに適用するコマンドをビルドおよび配置できます。  
  
 前から存在する場合にアクティブなプロジェクトには 3 種類の方法の 1 つがでキャプチャ :  
  
-   スタートアップ プロジェクト  
  
     ユーザーがキーを押すかまたは \[ビルド\] メニューから実行を選択したときに呼び出されるソリューションのプロパティ ページからプロジェクトを指定できます。  これは名前が太字フォントを持つソリューション エクスプローラーに表示されるという意味で古いアクティブなプロジェクトと同じように動作します。  
  
     オートメーション モデルのプロパティとして `DTE.Solution.SolutionBuild.StartupProjects` を呼び出してスタートアップ プロジェクトを取得できます。  VSPackage では<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> のメソッドを呼び出します。  `IVsSolutionBuildManager` は SID\_SVsSolutionBuildManager の `QueryService` によってサービスとして使用できます。  詳細については、「[プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)」および「[ソリューション構成](../../extensibility/internals/solution-configuration.md)」を参照してください。  
  
-   アクティブなソリューション ビルド構成  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] にアクティブなソリューション構成 `DTE.Solution.SolutionBuild.ActiveConfiguration` を実装してオートメーション モデルがあります。  ソリューション構成によってソリューション内の各プロジェクトの 1 種類のプロジェクト構成を含むコレクションです \(各プロジェクトには複数の構成が異なる名前を持つ複数のプラットフォームであることができます。  ソリューションのプロパティ ページに関する詳細については[ソリューション構成](../../extensibility/internals/solution-configuration.md) を参照してください。  
  
-   現在選択されているプロジェクト  
  
     プロジェクト階層を取得し選択した項目をプロジェクトに <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> のメソッドを実装します。  DTE から`SelectedItems.SelectedItem.Project` と `SelectedItems.SelectedItem.ProjectItem` のメソッドを使用します。  コア [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のドキュメントの見出しの下サンプル コードがあります。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)