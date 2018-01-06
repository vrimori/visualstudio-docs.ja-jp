---
title: "プロジェクトのモデルのコア コンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d2de7b73238589786c1e8a4ba42389201123c2b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-model-core-components"></a>プロジェクト モデルのコア コンポーネント
次の表は、プロジェクトのモデルに展開されます。 テーブルは、インターフェイスと、モデルとインターフェイス、および特定のオブジェクトに関連付けられているサービスで識別されるサービスの簡単な説明を表示します。 さらに、テーブルには、プロジェクトの作成と、特定のプロジェクトの種類の要件に応じて保守に省略可能な他のインターフェイスが詳しく説明します。  
  
 詳細については、次を参照してください。[をサポートするシンボル閲覧ツール](../../extensibility/internals/supporting-symbol-browsing-tools.md)です。  
  
### <a name="package-object"></a>パッケージ オブジェクト  
  
|Interface|コメント|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE に VSPackage を初期化し、IDE、そのサービスを利用できるようにします。|  
  
### <a name="project-factory-object"></a>プロジェクト ファクトリ オブジェクト  
  
|Interface|コメント|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|新しいプロジェクトの作成と既存のプロジェクトを開いて管理します。|  
  
### <a name="project-objects"></a>プロジェクトのオブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|加算とプロジェクト項目の削除の管理、エディターに対しを開き、各ドキュメント モニカーの間のマッピングを保持し、`VSITEMID`です。 継承`IVsProject`と`IVsProject2`です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|ナビゲーションおよび表示プロパティを管理し、イベントを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|により、コマンドの実行と類似の`IOleCommandTarget`切り取りや名前の変更などのフォーカスがソリューション エクスプ ローラーであるときのみに適用されるコマンドです。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|プロジェクトの階層のプライマリ コマンドのターゲット インターフェイスとして機能します。 これは、コマンドの状態または状態と実行中のコマンド用のオブジェクトを照会するための標準インターフェイスです。 いないプロジェクト ウィンドウに注目しているときに使用できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|プロジェクトの状態の永続化を調整します。 通常、プロジェクトの状態は、プロジェクト ファイルとして格納されますが、されていないファイル ベース記憶域システムに適応できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|ディスクまたはその他のストレージ システム内のオブジェクト上のファイルとして、そのプロジェクト項目の持続性のすべての側面を管理対象のプロジェクトを有効にします。 `IVsPeristHierarchyItem2`インターフェイスを実装していない項目の使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>インターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|ソース コード コントロールとの相互作用を調整します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|構成情報を管理するプロジェクトを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|デバッグとリリース構成などのプロジェクト構成オブジェクトを管理します。 ビルド、配置、およびデバッグ操作は、プロジェクト構成オブジェクトによってコーディネートされます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|制御 (破壊的な) 削除オプションまたは削除 (非破壊的な) 階層アイテムの階層によって実装されます。 クエリのインターフェイスを呼び出す、`IVsHierarchyDeleteHandler`からインターフェイス、`IVsHierarchy`インターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|サポートするオブジェクトの実装のオプションを提供、`IVsCfgProvider2`インターフェイスを実装するプロジェクトのオブジェクトとは異なる COM id を`IVsHierarchy`インターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|省略可能なインターフェイスが他の開発者が拡張可能なプロジェクトを作成するために実装します。 `IVsProjectStartupServices`インターフェイスにより、プロジェクト ファイルと呼び出しにサード パーティのサービスの GUID を読み込むたびに、プロジェクトが読み込まれるように、プロジェクト ファイルに永続化する GUID を登録するサード パーティ製 VSPackage`QueryService`その GUID のです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|ソース階層によって実装される、`UIHierarchy`ウィンドウを切り取り、コピーなどのクリップボード操作を調整し、貼り付けます。 使用して、`AdviseClipboardHelperEvents`クリップボード イベントを登録するインターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|UI 階層ウィンドウのドラッグ アンド ドロップ操作中にそのデータ ソースの基準としたドラッグした項目に関する情報を提供します。 呼び出される、`IVsHierarchy`インターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|UI 階層ウィンドウのドラッグ アンド ドロップ操作中に、ドロップ ターゲットの基準としたドラッグした項目に関する情報を提供します。 呼び出される、`IVsHierarchy`インターフェイスです。|  
  
### <a name="configuration-object"></a>構成オブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|構成に関する情報を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|構成情報を管理するプロジェクトを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|デバッガーの制御下で実行するプロジェクトを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|他のプロジェクトの配置操作を実行する配置プロジェクトによって実装されます。|  
  
### <a name="configuration-builder-object"></a>構成ビルダー オブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|プロジェクト構成のビルド操作を管理します。|  
  
### <a name="additional-project-objects"></a>プロジェクト オブジェクトを追加  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|項目のプロパティの表示、**プロパティ**ウィンドウです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|展開の出力を表示します。|  
  
 次の表は、プロジェクトのモデルで定義されたサービスの簡単な説明を表示します。  
  
### <a name="services"></a>サービス  
  
|サービス|コメント|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|IDE でそのプロジェクト ファクトリが存在することを登録するプロジェクトの種類を実装する Vspackage によって使用されます。 VSPackage を呼び出す必要があります`QueryService`このサービスを提供し、そのプロジェクト ファクトリを登録時に`IVsPackage::SetSite`メソッドが呼び出されます。 場合、`SetSite`メソッドは呼び出されません、プロジェクトがインスタンス化されていません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|現在のソリューション、プロジェクトを列挙、新しいプロジェクトを作成、プロジェクトの変更の通知を受け取るおよびにする機能などの IDE の内部の組み込みの概念へのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|ソース管理に参加するプロジェクトによって呼び出されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|開いているドキュメントをプロジェクト項目の 1 つ以上が既に開かれているかどうかを特定のテーブルを保持します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|インターフェイスおよびを実際には、標準のエディターまたは特定のエディターを使用してプロジェクト項目を開くと呼ばれるメソッドが含まれています。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|必要なときに呼び出されるすべてのプロジェクトで追加、削除またはその項目の名前を変更します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|ファイルまたはディレクトリへの変更を管理し、選択したファイルがディスクに変更されたときにクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|項目をダーティまたはそれらを保存するには、すべてのプロジェクトとエディターによって呼び出される必要です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|プロジェクト構成のビルドと展開の操作の順序を管理します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|デバッグのほとんどのコントロールで使用される低レベルのデバッガー サービスへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|現在の選択に関する情報を Vspackage のアクセスを有効にできとの通信、**プロパティ**ウィンドウです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|作成し、ツール ウィンドウまたはドキュメント ウィンドウを列挙する機能や、ユーザーにエラーを報告する機能などの IDE の UI 関連の基本的な機能を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE のステータス バーへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|オートメーション モデルを実装するために使用します。 モデルでは、プロジェクト、戻りますできるようにするプロパティ オブジェクトは、そのオブジェクトのインスタンスを作成します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|階層内のプロジェクト オブジェクトにクリップボードのイベントを実装するために使用します。 `SVsUIHierWinClipboardHelper`できます正しくハンドルの切り取り、コピー、および貼り付け操作。|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [ビルド内にありません: HierUtil7 プロジェクト クラスを使用して、プロジェクトの種類 (C++) を実装するには](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)