---
title: IDE 定数 |Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23512005bed66550b4a1de0f0a2de830d9fb823b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498994"
---
# <a name="ide-constants"></a>IDE 定数

<xref:Microsoft.VisualStudio.VSConstants>クラスは、統合開発環境 (IDE) に固有し、ヘッダー ファイルでのみを以前に定義された定数を提供します。

## <a name="logical-and-physical-views"></a>論理および物理ビュー

|[値]|説明|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、この例では、コード ビュー。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、ここで設定可能な限り<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>デバッグ ビューと同じビューにマップされる<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、この場合**ビュー フォーム**デザイナーのビュー。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、この場合、エディター ファクトリの既定/プライマリ ビュー。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、このドキュメントまたはデータのテキスト エディターの表示。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドを使用するユーザー定義ビューを選択するユーザーを求められます。|

## <a name="editor-factory-flags"></a>エディター ファクトリ フラグ

|[値]|説明|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|最初のパラメーターとしてには、ビットごとに、古いフラグが結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド。|
|[CEF します。OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|最初のパラメーターのビットごとに結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド、エディター ファクトリが必要な修正プログラムを実行する必要がありますこれを示します。|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|最初のパラメーターのビットごとに結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドでは、このフラグは、相互排他の[CEF します。CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)します。|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|最初のパラメーターのビットごとに結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド、エディター ファクトリは、ユーザー インターフェイス (UI) を表示せず、エディターを作成する必要がありますこれを示します。|

## <a name="visual-studio-errors"></a>Visual Studio のエラー

|[値]|説明|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|非同期動作をインターフェイスによって返される定数と対象のオブジェクト ビジーです|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|エラーに固有である HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「互換性のないドキュメント データ」です。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「パッケージが読み込まれていません」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ことを示すと、「プロジェクトは既に存在します」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|エラーに固有である HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "プロジェクト構成に失敗しました"を示すと。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「プロジェクトは読み込まれていません」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|エラーに固有である HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「ソリューション既に開かれている」ことを示すと|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「ソリューションは開いていません」|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|配列を指定するためのパラメーターを持つビルド インターフェイスによって返される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput>インターフェイスが実装にのみ適用できるメソッドのすべての出力。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドは、ドキュメントがエディターで開くことができない形式にこの値を返します。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|ユーザーが [戻る] ボタンをヒットすることを示す HRESULT 値を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ウィザード。|

## <a name="visual-studio-constants"></a>Visual Studio の定数

|[値]|説明|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「プロジェクトを転送します」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|固有の定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]「ツールボックス マーカー」の|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|固有の定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用して通知メッセージを配信するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>メソッド モダリティの先頭を示します。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|固有の定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用して通知メッセージを配信するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>モダリティの終了位置を示すメソッド。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|固有の定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用して通知メッセージを配信するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>コマンド バーのメトリックが変更されたことを示すメソッド。|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|固有の定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]cookie が設定されていないことを示します。|
|[VSITEMID します。Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト項目がないことを表す項目の識別子。 この値は、現在選択されていないときに使用されます。|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]項目の識別子をプロジェクト階層のルートを表し、1 つの項目ではなく、階層全体を識別するために使用されます。|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]項目の識別子を表す、現在選択されている項目または項目で、階層のルートを含めることができます。|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 IDE のコンポーネントだけが選択されているでについて説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>を呼び出します。

|定数|[値]|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 新しい選択状態を示すために使用される定数。

|定数|[値]|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>コンポーネント セレクター ダイアログ定数

|定数|[値]|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>関連項目

- [プロジェクト システムを拡張するための IDE 定義コマンド](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)