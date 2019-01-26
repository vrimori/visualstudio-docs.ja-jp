---
title: プロジェクト モデルのコア コンポーネント |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d6940db78b1b3f358387651acff6f3a9f098b62
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957589"
---
# <a name="project-model-core-components"></a>プロジェクト モデルのコア コンポーネント
次の表は、プロジェクト モデルを展開します。 テーブルは、インターフェイスと、モデルとインターフェイス、および特定のオブジェクトに関連付けられているサービスで識別されたサービスの簡単な説明を提示します。 さらに、テーブルには、プロジェクトの作成と、特定のプロジェクトの種類の要件に応じて保守で省略可能なその他のインターフェイスについて詳しく説明します。  
  
 詳細については、次を参照してください。[をサポートしているシンボル参照ツール](../../extensibility/internals/supporting-symbol-browsing-tools.md)します。  
  
### <a name="package-object"></a>パッケージ オブジェクト  
  
|Interface|コメント|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE に VSPackage を初期化し、そのサービスを IDE で使用できるようにします。|  
  
### <a name="project-factory-object"></a>プロジェクト ファクトリ オブジェクト  
  
|Interface|コメント|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|新しいプロジェクトを作成して既存のプロジェクトを開くを管理します。|  
  
### <a name="project-objects"></a>プロジェクト オブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|加算とプロジェクト アイテムの削除を管理し、エディターを開き、各ドキュメント モニカーの間のマッピングを保持して、`VSITEMID`します。 継承`IVsProject`と`IVsProject2`します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|ナビゲーションおよび表示プロパティを管理し、イベントを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|有効コマンドの実行と類似の`IOleCommandTarget`切り取りおよび名前の変更などのフォーカスがソリューション エクスプ ローラーであるときのみに適用されるコマンド。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|プロジェクト階層のプライマリ コマンド ターゲットのインターフェイスとして機能します。 これは、コマンドの状態または状態と実行コマンドのオブジェクトに対するクエリの標準のインターフェイスです。 [プロジェクト] ウィンドウには注目されていないときに使用できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|プロジェクトの状態の永続化を調整します。 通常、プロジェクトの状態は、プロジェクト ファイルとして保存されますが、ファイル ベースでないストレージ システムに適応させることができます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|永続化のいずれかのファイルとしてディスクまたはその他のストレージ システム内のオブジェクトに、そのプロジェクト アイテムのすべての側面を管理するプロジェクトを有効にします。 `IVsPersistHierarchyItem2`インターフェイスを実装していない項目の使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>インターフェイス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|ソース コード管理との対話を調整します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|プロジェクト構成情報の管理を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|デバッグ/リリースの構成などのプロジェクト構成オブジェクトを管理します。 ビルド、デプロイ、およびデバッグ操作がプロジェクト構成オブジェクトを使用して調整されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|(破壊的な) の削除を制御または階層アイテムの (非破壊的な) のオプションを削除する階層によって実装されます。 クエリ インターフェイスを呼び出す、`IVsHierarchyDeleteHandler`からインターフェイス、`IVsHierarchy`インターフェイス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|サポートするオブジェクトの実装オプションを提供します、`IVsCfgProvider2`インターフェイスを実装するプロジェクトのオブジェクトよりも、別の COM id を`IVsHierarchy`インターフェイス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|省略可能なインターフェイスが他の開発者が拡張可能なプロジェクトを作成するために実装します。 `IVsProjectStartupServices`インターフェイスにより、プロジェクト ファイルと呼び出しにサード パーティのサービスの GUID を読み込むたびに、プロジェクトが読み込まれるように、プロジェクト ファイルに永続化する GUID を登録するためにサード パーティ VSPackage`QueryService`の GUID。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|ソース階層でによって実装される、`UIHierarchy`ウィンドウを切り取り、コピーなどのクリップボード操作を調整し、貼り付けます。 使用して、`AdviseClipboardHelperEvents`クリップボード イベントを登録するインターフェイス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|UI 階層ウィンドウで、ドラッグ アンド ドロップ操作中にそのデータ ソースの基準としたドラッグした項目について説明します。 呼び出される、`IVsHierarchy`インターフェイス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|UI 階層ウィンドウで、ドラッグ アンド ドロップ操作中にドロップ ターゲットに対するドラッグした項目について説明します。 呼び出される、`IVsHierarchy`インターフェイス。|  
  
### <a name="configuration-object"></a>構成オブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|構成に関する情報を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|プロジェクト構成情報の管理を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|デバッガーの制御下で実行するプロジェクトを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|他のプロジェクトの配置操作を実行する配置プロジェクトによって実装されます。|  
  
### <a name="configuration-builder-object"></a>構成ビルダー オブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|プロジェクト構成のビルド操作を管理します。|  
  
### <a name="additional-project-objects"></a>その他のプロジェクト オブジェクト  
  
|インターフェイス|コメント|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|表示項目のプロパティ、**プロパティ**ウィンドウ。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|デプロイの出力が表示されます。|  
  
 次の表は、プロジェクト モデルで識別されたサービスの簡単な説明を表示します。  
  
### <a name="services"></a>Services  
  
|サービス|コメント|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|IDE でそのプロジェクト ファクトリが存在するプロジェクトの種類を登録するを実装する Vspackage によって使用されます。 VSPackage を呼び出す必要があります`QueryService`このサービスし、そのプロジェクト ファクトリを登録するときに`IVsPackage::SetSite`メソッドが呼び出されます。 場合、`SetSite`メソッドが呼び出されなかった、プロジェクトがインスタンス化されません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|現在のソリューション、プロジェクトの列挙、新しいプロジェクトを作成、プロジェクトの変更に注意してください。 およびにする機能などの IDE の内部の組み込みの概念へのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|ソース管理に参加するプロジェクトによって呼び出されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|1 つ以上のプロジェクト項目が既に開かれているかどうかを判断する開いているドキュメントのテーブルを保持します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|インターフェイスと実際には、標準のエディターまたは特定のエディターを使用してプロジェクト項目を開くと呼ばれるメソッドが含まれています。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|必要なときに呼び出されるすべてのプロジェクトで追加、削除またはその項目の名前を変更します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|ファイルまたはディレクトリへの変更を管理し、選択したファイルがディスクに変更されたときにクライアントに通知します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|必要な項目がダーティかに保存する前に、すべてのプロジェクトとエディターによって呼び出されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|プロジェクト構成のビルドと展開の操作の順序を管理します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|ほとんどのデバッグ コントロールで使用される低レベル デバッガー サービスへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|現在の選択に関する情報にアクセスを Vspackage との通信を可能、**プロパティ**ウィンドウ。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|作成し、ツール ウィンドウまたはドキュメント ウィンドウを列挙する機能や、ユーザーに、エラーを報告する機能などの IDE の UI 関連の基本的な機能を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE のステータス バーへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|オートメーション モデルを実装するために使用します。 プロジェクト モデルを返すはできるようにするプロパティ オブジェクトは、そのオブジェクトのインスタンスを作成します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|プロジェクト オブジェクト階層内のクリップボードのイベントを実装するために使用します。 `SVsUIHierWinClipboardHelper` できます正しくハンドルの切り取り、コピー、および貼り付け操作。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [チェックリスト:新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [: ビルドに存在しませんHierUtil7 プロジェクト クラスを使用して、プロジェクトの種類 (C++) を実装するには](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)