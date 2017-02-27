---
title: "プロジェクト モデルのコア コンポーネント | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト モデルやオブジェクト インターフェイス"
  - "プロジェクト モデルでは、サービス"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# プロジェクト モデルのコア コンポーネント
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次の表はプロジェクト モデルに配置します。  モデルで指定されるインターフェイスのテーブルの現在の簡単な説明とサービスおよび特定のオブジェクトに関連付けられたインターフェイスおよびサービス。  またテーブルは特定の種類のプロジェクトの要件に基づいてプロジェクトの作成と保守のオプションのそのほかのインターフェイスについて詳しく説明します。  
  
 詳細については、「[シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)」を参照してください。  
  
### パッケージ オブジェクト  
  
|Interface|コメント|  
|---------------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE の VSPackage を初期化しサービスを IDE で使用できるようにします。|  
  
### プロジェクト ファクトリ オブジェクト  
  
|Interface|コメント|  
|---------------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|新しいプロジェクトを作成したり既存のマネージ プロジェクトを開きます。|  
  
### プロジェクトのオブジェクト  
  
|インターフェイス|コメント|  
|--------------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|プロジェクト項目を開きエディターの追加と削除を管理し各ドキュメント `VSITEMID` モニカーとの間のマップを保持します。  `IVsProject` と `IVsProject2` から継承します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|のナビゲーション管理および \[プロパティとイベントを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|フォーカスがソリューション エクスプローラーにある場合のみ適用するコピーと名前の変更などコマンドの `IOleCommandTarget` のようなコマンドを実行できるようにします。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|基本コマンドの対象として機能はプロジェクト階層のインターフェイスします。  これはコマンドの状態のオブジェクトや状態および実行するコマンド照会するための標準インターフェイスです。  プロジェクトのウィンドウで明確でない場合に使用できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|プロジェクトの状態の永続性を調整します。  通常プロジェクトの状態はプロジェクト ファイルとして保存されますがファイル ベースではないストレージ システムに対応できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|他のストレージ システムのディスクまたはオブジェクト ファイルとしてプロジェクト項目の永続化のあらゆる面を管理するプロジェクトを有効にします。  `IVsPeristHierarchyItem2` のインターフェイスは <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> のインターフェイスを実装しない項目に対して使用されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|ソース・コード管理とのやり取りを管理します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|構成情報を管理できるようにプロジェクト。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理はデバッグまたはリリース構成など構成オブジェクトを返します。  ビルド配置およびデバッグ操作にはプロジェクト構成オブジェクトを介して調整されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|削除 \(有害なコントロール\) または \(階層の項目の非破壊的なオプションを削除するには階層によって実装されます。  `IVsHierarchy` のインターフェイスから `IVsHierarchyDeleteHandler` のインターフェイスを取得できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|プロジェクトのオブジェクトとは異なる COM ID の `IVsCfgProvider2` のインターフェイスを実装する `IVsHierarchy` インターフェイスをサポートするオブジェクトを作成するの実装方法を示します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|プロジェクトを拡張できるようにするために他の開発者によって実装されるインターフェイスと省略可能。  `IVsProjectStartupServices` のインターフェイスは毎回プロジェクトを読み込むようにプロジェクト ファイルにその GUID のプロジェクト ファイルと呼び出し `QueryService` に読み込みサードパーティのサービスの GUID を保持する GUID の登録をサードパーティの VSPackage ができます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|切り取りコピー貼り付けなどのクリップボード操作を調整するために `UIHierarchy` のウィンドウでソースの階層によって実装されます。  クリップボードのイベントを登録するために `AdviseClipboardHelperEvents` のインターフェイスを使用します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|UI 階層のペインのドラッグ アンド ドロップ操作中にデータ ソースに関連してドラッグした項目に関する情報を提供します。  `IVsHierarchy` のインターフェイスから呼び出されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|UI 階層のペインのドラッグ アンド ドロップ操作中にドロップ ターゲットとしてドラッグした項目に関する情報を提供します。  `IVsHierarchy` のインターフェイスから呼び出されます。|  
  
### 構成オブジェクト  
  
|インターフェイス|コメント|  
|--------------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|構成について説明します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|構成情報を管理できるようにプロジェクト。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|デバッガーの制御下に実行するプロジェクトを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|他のプロジェクトの配置操作を実行する配置プロジェクトによって実装されます。|  
  
### ビルダー オブジェクトの構成  
  
|インターフェイス|コメント|  
|--------------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|プロジェクト構成のビルドと対話します。|  
  
### プロジェクト オブジェクトの追加  
  
|インターフェイス|コメント|  
|--------------|----------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|\[ENT0ENT\] ウィンドウの項目のプロパティを表示します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|配置用の出力。|  
  
 プロジェクトで指定されるサービスを次の表についての簡単な説明がシミュレートします。  
  
### サービス  
  
|サービス|コメント|  
|----------|----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|VSPackage で使用されるプロジェクト ファクトリはIDE であることを登録するためにプロジェクトを実行できます。  VSPackage は `IVsPackage::SetSite` のメソッドが呼び出されたときにこのサービスの `QueryService` を呼び出しプロジェクト ファクトリを登録する必要があります。  `SetSite` のメソッドが呼び出された場合プロジェクトはインスタンス化できません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|プロジェクトを列挙する機能など現在のソリューションの組み込みの概念を内部IDE'S へのアクセスを提供します。新しいプロジェクトの作成プロジェクトの変更などに注意します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|ソース管理に参加するプロジェクトによって呼び出されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|開いているドキュメントのテーブルをプロジェクト項目の一つ以上が既に開くかどうかを判断するために保持されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|実際に標準エディターまたは特定のエディターを使用してプロジェクト項目を開くために呼び出されるメソッドおよびインターフェイスが含まれています。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|ユーザーが追加したすべてのプロジェクトで呼び出すために必要な項目を削除したり名前を変更します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理はファイルやディレクトリに選択したファイルがディスク上で変更されて変更しクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|すべてのプロジェクトおよびエディターによって呼び出されるために必要とされる前にダーティ項目または変更を保存します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|プロジェクト構成のビルドと配置の操作順序を管理します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|ほとんどのコントロールのデバッグに使用する低レベルのデバッガー サービスへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|\[ENT0ENT\] ウィンドウのを使用して現在の選択を有効の通信に関する情報へのアクセスの VSPackages。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|作成してツール ウィンドウまたはドキュメント ウィンドウを列挙したりユーザーにエラーを通知する機能など基本的な UI 関連の IDE 機能を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE のステータス バーへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|オートメーション モデルを実装するために使用します。  プロジェクト モデルではオブジェクトのインスタンスを作成できるプロパティ オブジェクトを返します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|階層のプロジェクトのオブジェクトのクリップボードのイベントを処理するために使用します。  `SVsUIHierWinClipboardHelper` は切り取りコピーおよび貼り付け操作の処理を正しくできます。|  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/ja-jp/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)