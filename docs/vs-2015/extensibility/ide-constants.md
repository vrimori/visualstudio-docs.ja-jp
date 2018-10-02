---
title: IDE 定数 |Microsoft Docs
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
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1a791dd1190bc083d2be398d88722daa227cf12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537947"
---
# <a name="ide-constants"></a>IDE 定数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDE 定数](https://docs.microsoft.com/visualstudio/extensibility/ide-constants)します。  
  
<xref:Microsoft.VisualStudio.VSConstants>クラスは、統合開発環境 (IDE) に固有し、ヘッダー ファイルでのみを以前に定義された定数を提供します。  
  
## <a name="logical-and-physical-views"></a>論理および物理ビュー  
  
|[値]|説明|  
|-----------|-----------------|  
|[LOGVIEWID_Code_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.code_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、この例では、選択可能なコード ビュー。|  
|[LOGVIEWID_Debugging_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.debugging_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、ここで設定可能な限り<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>デバッグ ビューと同じビューにマップされる<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>。|  
|[LOGVIEWID_Designer_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.designer_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、この場合**ビュー フォーム**デザイナーのビュー。|  
|[LOGVIEWID_Primary_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.primary_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、この場合、エディター ファクトリの既定/プライマリ ビュー。|  
|[LOGVIEWID_TextView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.textview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>を取得するメソッド、**プログラムから開く**ダイアログ ボックスで、このドキュメントまたはデータのテキスト エディターの表示。|  
|[LOGVIEWID_UserChooseView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.userchooseview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドを使用するユーザー定義ビューを選択するユーザーを求められます。|  
  
## <a name="editor-factory-flags"></a>エディター ファクトリ フラグ  
  
|[値]|説明|  
|-----------|-----------------|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|最初のパラメーターとしてには、ビットごとに、古いフラグが結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド。|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|最初のパラメーターのビットごとに結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド、エディター ファクトリが必要な修正プログラムを実行する必要がありますこれを示します。|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|最初のパラメーターのビットごとに結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドでは、このフラグは、相互排他の[CEF します。CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)します。|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|最初のパラメーターのビットごとに結合、<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド、エディター ファクトリは、ユーザー インターフェイス (UI) を表示せず、エディターを作成する必要がありますこれを示します。|  
  
## <a name="visual-studio-errors"></a>Visual Studio のエラー  
  
|[値]|説明|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|非同期動作をインターフェイスによって返される定数と対象のオブジェクト ビジーです|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|エラーの「互換性のないドキュメント データ」の Visual Studio に固有である hresult 値。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|エラーの Visual Studio に固有である hresult 値が「パッケージが読み込まれていない」ことを示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio に固有である HRESULT エラーが示す、「プロジェクトは既に存在します」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|エラーの hresult 値は、Visual Studio に固有では、"プロジェクト構成に失敗しました"ことを示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|エラーの Visual Studio に固有である hresult 値が「プロジェクトが読み込まれていない」ことを示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio に固有である HRESULT エラーは、「ソリューション既に開いている」ことを示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|エラーの hresult 値は、Visual Studio に固有では、「ソリューションを開けません」ことを示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|配列を指定するためのパラメーターを持つビルド インターフェイスによって返される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput>インターフェイスが実装にのみ適用できるメソッドのすべての出力。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドは、ドキュメントがエディターで開くことができない形式にこの値を返します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|ユーザーが Visual Studio のウィザードの [戻る] ボタンをヒットすることを示す HRESULT 値。|  
  
## <a name="visual-studio-constants"></a>Visual Studio の定数  
  
|[値]|説明|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|エラーの Visual Studio に固有である hresult 値が「プロジェクトが転送された」ことを示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|「ツールボックス マーカー」for Visual Studio に固有である定数|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|使用して通知メッセージを配信するために Visual Studio 固有の定数、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>メソッド モダリティの先頭を示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|使用して通知メッセージを配信するために Visual Studio 固有の定数、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>モダリティの終了位置を示すメソッド。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|使用して通知メッセージを配信するために Visual Studio 固有の定数、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>コマンド バーのメトリックが変更されたことを示すメソッド。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Cookie が設定されていないことを示す Visual Studio に固有の定数。|  
|[VSITEMID します。Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|プロジェクト項目がないことを表す Visual Studio の項目の識別子です。 この値は、現在選択されていないときに使用されます。|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|プロジェクト階層のルートを表し、1 つの項目ではなく、階層全体を識別するために使用されますが、Visual Studio 項目識別子です。|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|現在選択されている項目または階層のルートを含めることができますの項目を表す Visual Studio 項目の識別子です。| 
  
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
 [プロジェクト システムを拡張するための IDE 定義コマンド](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

