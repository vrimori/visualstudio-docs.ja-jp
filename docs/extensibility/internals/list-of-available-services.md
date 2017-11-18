---
title: "使用可能なサービスのリスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f2fca0baa747311b08983d8fc7e30efd02ae4c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="list-of-available-services"></a>使用可能なサービスの一覧
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Visual Studio SDK は、次のサービスをサポートします。 一部のパッケージは、ここに記載されていない、独自のサービスを提供して — など、言語サービスには 1 つのサービス GUID はありません。 言語の名前を使用して、レジストリに言語サービスの GUID を見つける必要があります。  
  
 次のとおり、またはその他のソース (たとえば、言語サービス) から取得したサービス Guid を使用すると、プライマリ インターフェイスまたはサービスごとに示されるインターフェイスを取得します。  
  
## <a name="the-services"></a>サービス  
  
|サービス|インターフェイス|Visual Studio|Visual Studio 2005|説明|  
|-------------|---------------|-------------------|------------------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SBindHost>|<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>|はい|はい|Vspackage を取得するために使用する<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>を非同期のデータ転送を容易にする ActiveX コントロールからのインターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDTE>|<xref:EnvDTE.DTE>|いいえ|はい|自動化に使用するデザイン時の機能拡張 (DTE) オブジェクトを取得します。<br /><br /> C と C++ ID: SID_SDTE|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate>|<xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate>|はい|はい|コントロールの既定のイベント ハンドラーを表示するフォーム デザイナーによって実装されます。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch>|IDispatch|はい|はい|VSPackage、オートメーション インターフェイスに別の VSPackage またはコントロールのアクセスを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib>|はい|はい|追加または拡張型ライブラリを作成する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDirList>|<xref:Microsoft.VisualStudio.Shell.Interop.IDirList>|いいえ|はい|コンテナーへのアクセスには、リストの一覧の名前付きを提供します。たとえばのようにを検索するディレクトリの一覧、**検索し、置換** ダイアログ ボックスで、**検索対象の**ドロップダウン リスト。 <xref:Microsoft.VisualStudio.Shell.Interop.IDirList>オブジェクトする読み書きしたりできるように書き込まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner>|はい|はい|動的に表示または非表示、独自のツール ウィンドウに VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager>|<xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager>|はい|はい|有効にするを示すために VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ライセンス キーの一覧を指定することによって必要なクラスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>|はい|はい|により、ローカルの基準としたレジストリにアクセスする VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]レジストリ ハイブです。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager>|はい|はい|メッセージ ループ、キーボード ループ、およびイベント通知などのコンポーネントの調整サービス提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>|はい|はい|さまざまなユーザー インターフェイス (UI) 要素にアクセスする VSPackage を有効に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ヘルプ、ステータス バー、および UI イベントなどです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|はい|はい|UI に UI と統合する VSPackage を有効に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite>|はい|はい|ツールに固有の UI の変更を制御する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>|はい|はい|そのコンテナーの元に戻すスタックに参加するか、またはそのコンテナーの元に戻すスタックにアクセスする、コンテナーの undo マネージャーにアクセスする VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>|はい|はい|独自のサービスを提供する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib>|はい|はい|タイプ ライブラリを参照できるようにするフォーム デザイナーを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>|はい|はい|選択コンテナーの選択項目へのアクセスを提供します。 フォーム デザイナーによって使用されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|はい|はい|コマンド ハンドラー チェーンに参加し、統合開発環境 (IDE) または自体に代わってコマンドを処理する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale>|<xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale>|はい|はい|ホストの UI のロケール情報へのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>|いいえ|はい|ログ記録がオンにすると、高度なメッセージを記録する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg>|はい|はい|アクセスできるように、**プロジェクト項目の追加** ダイアログ ボックスを実装する Vspackage 独自**項目の追加**メニュー オプション。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg>|はい|はい|表示、**参照の追加** ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>|はい|はい|Devenv.exe にコマンド ライン スイッチで指定されたかどうかを決定する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser>|いいえ|はい|により、新しい VSPackage**呼び出しブラウザー**のデバッグに使用します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView>|はい|はい|同期するために VSPackage をできるように、**クラス ビュー**特定のオブジェクトにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping>|はい|はい|Guid とコマンド名をマップし、すべての利用可能なコマンドと名前の名前を決定するのには、サポートを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView>|いいえ|はい|操作する VSPackage をできるように、**コード定義ビュー**です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler>|はい|はい|内部サービス。 使用しないでください。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|はい|はい|1 つまたは複数のドキュメントを含めることができるコード ウィンドウへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|はい|はい|ドロップダウン バーなどのコード ウィンドウに変更を追加する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2>|はい|はい|コマンドを実行する VSPackage を有効に、**コマンド ウィンドウ**し、それ以外の場合との対話、**コマンド ウィンドウ**します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection>|いいえ|はい|一覧を操作する VSPackage を有効に**コマンド**で保持されている windows[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager>|はい|はい|参照情報を提供する VSPackage をできるように、**オブジェクト ブラウザー**です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg>|いいえ|はい|により、サポートするために VSPackage、**参照の追加**オプションは、ユーザーがプロジェクトに追加する外部のコンポーネントを選択できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2>|いいえ|はい|により、サポートするために VSPackage、**参照の追加**オプションは、ユーザーがプロジェクトに追加する外部のコンポーネントを選択できます。 ダイアログ ボックスのこのバージョンにより、表示される前に、コンポーネント リストの情報を事前設定します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg>|いいえ|はい|表示、 **Configuration Manager**  ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject>|いいえ|はい|他のプロジェクトのコレクションを格納するプロジェクトを作成する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol>|はい|はい|特定のデバッグ エンジンを開始する、IDE で使用されるデバッグ可能なプロトコルの一覧を更新する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch>|はい|はい|デバッガーの起動をサポートする VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>|はい|はい|Web services の検出に使用される探索セッションを作成する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>|はい|はい|作成するファクトリを提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>階層 (プロジェクト) を指定するオブジェクトを列挙するために使用します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList>|いいえ|はい|操作するための他のメソッドを提供、**エラー一覧の構築**タスク一覧 ウィンドウ。 具体的には、表示、**エラー一覧の構築**forefront タスク ウィンドウ強制的に表示されるすべてのエラーとします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager>|はい|はい|アクセスできるように、**その他のファイル**現在のソリューションのプロジェクト ノードです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>||はい|はい|互換性のために残されています。 使用して`SVsFileChangeEx`代わりにサービスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>|はい|はい|IDE によってトリガーされるさまざまなファイルの変更イベントにアクセスするために VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>|はい|はい|により、項目をフィルター処理に表示される VSPackage、**項目の追加** ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys>|はい|はい|高度なキーボードのフィルター処理を実行する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>|いいえ|はい|フォントのキャッシュのセットへのアクセスを提供し、色の[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]更新またはオフに特定のキャッシュまたはすべてのキャッシュします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>|はい|はい|により、VSPackage によって保持されているフォントと色の設定を操作する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 さらに、このサービスは、フォントおよびカラーのデータを操作するためのユーティリティ メソッドのコレクションへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>|はい|はい|全般 にアクセスできるように**出力ウィンドウ** ウィンドウで、必要に応じて作成します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem>|はい|はい|ヘルプ システムへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter>|はい|はい|によって使用される、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーにその出力をフォーマットする HTML のハンドル。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIME>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIME>|はい|はい|入力方式エディター (IME) API を VSPackage 内でアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp>|<xref:Microsoft.VisualStudio.VSHelp.SVsHelp>|はい|はい|アクセスできるように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ヘルプ キーワードまたは URL のシステムへのアクセス ナビゲーション コントロールだけでなく、ヘルプ ファイルを使用します。 このサービスは、ヘルプに統合されている場合にのみ使用可能な[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 外部プログラムとして実行されていないとします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler>|はい|はい|マウス ホイールを使用して、マウスのホイールがクリックされたときに、スクロール、パンのビットマップを処理などの IntelliMouse 機能にアクセスするために VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine>|いいえ|はい|ロードまたは IntelliSense 操作のサポートの一部としてファイルをアンロードするプロジェクト階層ノードを有効にします。 読み込みとアンロード、プロジェクトの IntelliSense のツールヒントに表示される内容に影響を与えるトリガー イベントを処理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost>|いいえ|はい|により、プロジェクト階層ノードは、入れ子になった IntelliSense プロジェクトに関する情報を提供 (実装する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>インターフェイス) を IntelliSense のツールヒントに表示できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager>|いいえ|はい|参照または IntelliSense のツールヒントに表示される内容に影響する可能性の構成の変更などのイベントのリスナーに通知する、プロジェクト階層ノードを有効にします。 格納されている言語で使用するよう設計されています。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>|はい|はい|VSPackage は、「非表示」のエディターを登録する完全な編集機能を提供がないユーザーに表示するエディターを使用できます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|はい|はい|データのヒントなどのテキスト ビュー、および単語の範囲に追加情報を提供する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>|はい|はい|出力が、出力ウィンドウに送信されたコマンド ライン プログラムを実行し、標準的な警告およびエラー ウィンドウに送信されるエラー メッセージを解析、一時的なバッチ スクリプトを実行する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory>|はい|はい|作成するためのファクトリを提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>オブジェクト。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>|はい|はい|リンクされた undo マネージャーへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory>|はい|はい|共有メニュー エディターにアクセスするフォーム デザイナーを有効にします。 IVsMenuEditorFactory できますを照会する<xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor>です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>|はい|はい|バッグを作成する"コンテキスト"、特定のコンテキストのヘルプ キーワードを関連付けるために使用するために VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser>|はい|はい|により、特定のオブジェクトに移動する VSPackage、**オブジェクト ブラウザー**です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager>|はい|はい|場合は、そのライブラリ マネージャーを登録する VSPackage を有効に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]名前空間、クラスと列挙などのオブジェクトを管理するためです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch>|はい|はい|特定のオブジェクトを検索する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg>|いいえ|はい|により、標準を使用する VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトまたはソリューションを開く ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>|はい|はい|VSPackage、一般出力ウィンドウに追加の出力ウィンドウの作成を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine>|はい|はい|によりの実行者、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンドラインを解析するインターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver>|いいえ|はい|固有の変数を解決する方法を提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]最終的なパスを生成するためにパスに埋め込まれているとします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService>|いいえ|はい|表示、**変更のプレビュー**  ダイアログ ボックスのコードのリファクタリングのために使用します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager>|いいえ|はい|プロファイル マネージャーにアクセスできるように[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]をインポートして設定データをエクスポートすると、現在のユーザーのプロファイル設定の UI を表示できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI>|いいえ|はい|現在のユーザーのプロファイル設定を表示するダイアログ ボックスが表示されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame>|はい|はい|オーバーライドするプロパティ ページが最初に表示する VSPackage をできるように、**プロパティ**ウィンドウです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|いいえ|はい|メモリ内で変更または保存するのには、ファイルをソース管理プロバイダーを通知するために Vspackage によって使用されます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider>|いいえ|はい|プログラムによって、デバッガー内で実行するようにターゲットをオーバーライドする VSPackage プロジェクトを有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>|はい|はい|IDE でエディター ファクトリを登録する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope>|いいえ|はい|検索スコープを登録する VSPackage をできるように、**ファイル内の検索** ダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>|はい|はい|すべてのコマンドを表示する VSPackage をにより、優先度の高いコマンド ハンドラーとして登録する VSPackage を有効にします。 すべての場合は、慎重を使用します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>|はい|はい|IDE でプロジェクトの種類を登録する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager>|いいえ|はい|サテライト Dll からマネージ コードとアンマネージ リソースを読み込み、VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView>|はい|はい|使用して<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>代わりにサービスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>|はい|はい|アクセスを IDE を実行しているドキュメント テーブル (RDT) をすべて現在追跡を開いたドキュメントを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|いいえ|はい|ソース管理に参加できるようにソース管理プロバイダーに登録する Vspackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|はい|はい|取得およびソース管理プロバイダー オプションを設定するために VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>|いいえ|はい|ユーザーのプロファイルの設定に読み取りアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell>|はい|はい|直接対話して、その他の Vspackage を操作する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger>|はい|はい|アクセスできるように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|はい|はい|現在の選択範囲にアクセスし、コマンド UI コンテキストを管理する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider>|IVSMDCodeDomProvider|いいえ|はい|ネイティブ コードで使用できるコード ドキュメント オブジェクト モデル (DOM) プロバイダーにアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService>|IVSMDCodeDomCreator<br /><br /> IVSMDDesignerService|いいえ|はい|管理対象のフォーム デザイナーには、IDE のサポートへのアクセスを提供します。 `IVSMDCodeDomCreator`コード DOM プロバイダーを作成するために使用できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser>|IVSMDPropertyBrowser|いいえ|はい|デザイナーのプロパティの windows サービスへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService>|いいえ|はい|返すことができるインターフェイスへのアクセスを提供する<xref:System.ComponentModel.Design.ITypeResolutionService>ネイティブ コードで使用可能なオブジェクトです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope>|いいえ|はい|必要に応じて、ロックを考慮して、アセンブリのスコープを表示する方法を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|はい|はい|現在のソリューションに最上位レベルのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager>|はい|はい|ソリューションのビルド プロセスと対話する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|はい|はい|使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>代わりにサービスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>|はい|はい|保存し、現在のソリューションの .sln ファイルから情報を取得する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences>|いいえ|はい|では、追加し、マネージ コード アセンブリの参照を更新します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload>|いいえ|はい|開始およびバック グラウンド スレッドでダウンロード サービスを停止するためのスタート ページのダウンロード サービスへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>|はい|はい|IDE のステータス バーへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys>|いいえ|はい|マネージ コード アセンブリの署名で使用されるパスワードで強力なキー名とキー ファイルを作成するためのメソッドへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO>|はい|はい|複数の形式でデータを保存するためのサポートを提供する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>|はい|はい|タスク一覧ウィンドウを IDE のアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities>|いいえ|はい|テキスト ファイルの読み込みと保存には、ユーティリティを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>|はい|はい|すべてのテキスト バッファーだけでなく、IDE で使用可能な (非表示の領域) の非表示テキスト セッションへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut>|はい|はい|Win32 のバージョンを提供`TextOut`デバイス コンテキスト (DC ハンドルが必要です) にテキストを書き込むための関数。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet>|はい|はい|テキストの画像またはバッファー内のテキスト範囲の一覧へのアクセスを提供します。 このサービスは、通常、ドキュメントのコンテナーに実装しに現在のドキュメントを参照します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog>|いいえ|はい|(バック グラウンド タスクの待機に使用) 別のスレッドが待機するダイアログ ボックスを表示する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool>|いいえ|はい|により、VSPackage によって保持し、バック グラウンド タスクを開始する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>|はい|はい|IDE にアクセスできるように**ツールボックス**です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>|はい|はい|情報を取得する VSPackage を有効に**ツールボックス**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry>|いいえ|はい|により、全体を事前読み込みのパフォーマンス コストをかけずにツールボックス データ プロバイダーを登録する VSPackage**ツールボックス**です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions>|いいえ|はい|有効にするかどうかを VSPackage、**オプション** ダイアログ ボックスが開いていると、すべてのオプション ページの表示を更新します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|いいえ|はい|プロジェクトのファイルの変更を監視し、バッチのソース管理プロバイダーに制御を提供する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|はい|はい|現在選択されているプロジェクト アイテムに影響を与える選択への変更の IDE に通知するために VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper>|はい|はい|他の階層を使用して、クリップボードの使用を調整するには、VSPackage プロジェクトの場合) などの階層を使用できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>|はい|はい|ツール ウィンドウおよびドキュメント ウィンドウなどの IDE の UI 要素へのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr>|はい|はい|データのストリームの内容に基づくすべてのウィンドウの位置を復元するか、すべてのウィンドウの位置をストリームに保存する VSPackage を有効にします。 ほとんど使用しません。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>|はい|はい|さまざまな方法でドキュメントを開くと、どのようなドキュメントの所有者を決定する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>|いいえ|はい|実装によって使用される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>レポート エラーおよび情報メッセージへのインターフェイスです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService>|はい|はい|VSPackage を作成およびという Web 閲覧セッションの制御を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites>|はい|はい|により、ユーザーの追加する VSPackage**お気に入り** ボックスの一覧です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview>|はい|はい|子ウィンドウに通常の Web ページをプレビューする VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU>|はい|はい|Url の最も最近使用した (MRU) の一覧に URL を追加して、MRU 一覧のすべての Url の一覧を取得する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>|はい|はい|パッケージまたはパッケージの一部を配置する場合がありますをウィンドウ フレームを取得する VSPackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService>|はい|はい|特定のメタデータ ファイルに関連付けられている XML 形式のドキュメントのファイルへのアクセスを提供します。|  
  
## <a name="see-also"></a>関連項目  
 [COM および管理サービス](http://msdn.microsoft.com/en-us/6c5808b4-ad87-48d7-ae06-33a81e7052af)   
 [サービスの使用と提供](../../extensibility/using-and-providing-services.md)