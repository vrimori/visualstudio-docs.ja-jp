---
title: "IDE 定数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE のエラー"
  - "論理的なビュー"
  - "IDE のエラー [Visual Studio]"
  - "UI コンテキスト定数"
  - "Visual Studio IDE の定数"
  - "IDE、定数"
  - "物理ビュー"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE 定数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.VSConstants> クラスには、統合開発環境 \(IDE\) に固有およびとヘッダー ファイル内でだけを上記で定義した定数が用意されています。  
  
## 論理的および物理的なビュー  
  
|値|説明|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 取得するメソッド、 **ファイルを開く** 選択可能なコード ビューでは、この場合のダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 取得するメソッド、 **ファイルを開く** ダイアログ ボックスで、ここで設定可能な <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> デバッグと同じビューにマップされるビュー <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>します。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 取得するメソッド、 **ファイルを開く** をここでは、ダイアログ ボックス **フォームの表示** デザイナーのビューです。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 取得するメソッド、 **ファイルを開く** ここエディター ファクトリの既定\/プライマリ ビューのダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 取得するメソッド、 **ファイルを開く** ドキュメントまたはデータのテキスト エディターのビューののダイアログ ボックス。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> メソッドを使用するユーザー定義ビューを選択するユーザーが求められます。|  
  
## エディター ファクトリ フラグ  
  
|値|説明|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|古いフラグの組み合わせとして、最初のパラメーターのビットごとの <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> メソッドです。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|最初のパラメーターとしてビットごとの <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, 、メソッド、これによって示されるエディター ファクトリのために必要な修正を行う必要があります。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|最初のパラメーターとしてビットごとの <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> メソッドでは、このフラグは、相互排他の <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>です。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|最初のパラメーターとしてビットごとの <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> メソッド、これによって示されるエディター ファクトリは、ユーザー インターフェイス \(UI\) を表示することがなく、エディターを作成する必要があります。|  
  
## Visual Studio でエラー  
  
|値|説明|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|非同期動作するインターフェイスによって返される定数ときに、対象のオブジェクト ビジーです|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "互換性のないドキュメント data"にします。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「パッケージが読み込まれていない」を示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ことを示すと、「プロジェクト既に存在します」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "プロジェクト構成に失敗しました"を示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「プロジェクトが読み込まれていない」を示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「ソリューション既に開かれている」を示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「ソリューションは開いていません」を示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|配列を指定するためのパラメーターを持つビルド インターフェイスによって返される、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> インターフェイスも、実装にのみ適用できるメソッドのすべての出力です。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> メソッドは、ドキュメントがエディターで開くことができない形式にこの値を返します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|ユーザーが \[戻る\] ボタンを押すことを示す HRESULT 値、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ウィザード。|  
  
## Visual Studio 定数  
  
|値|説明|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|エラーの hresult 値に固有である [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "Project 転送"を示します|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|固有である定数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「ツールボックス マーカー」について|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|固有である定数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して通知メッセージを配信するため、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> モダリティの先頭を示すメソッドです。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|固有である定数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して通知メッセージを配信するため、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> モダリティの末尾を示す方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|固有である定数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して通知メッセージを配信するため、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> コマンド バーの測定値が変更されていることを示すメソッドです。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|固有である定数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cookie が設定されていないことを示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト項目がない場合を表す項目の識別子。 この値は、現在選択されていないときに使用されます。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト階層のルートを表し、1 つの項目ではなく、階層全体を識別するために使用する項目の識別子。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目の識別子を表す、現在選択されている項目が、階層のルートを含めることができます。|  
  
## IVsSelectionEvents  
 IDE のコンポーネントはどれだけが選択されているの説明、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> を呼び出します。  
  
|定数|値|  
|--------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0x2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0x4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0x3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0x0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0x5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0x1|  
  
## VSSELELEMID  
 新しい選択状態を示すために使用する定数。  
  
|定数|値|  
|--------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## コンポーネントの選択\] ダイアログの定数  
  
|定数|値|  
|--------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER \+ 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER \+ 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER \+ 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER \+ 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER \+ 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER \+ 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER \+ 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER \+ 1289|  
  
## 参照  
 [プロジェクト システムを拡張するための IDE 定義のコマンド](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)