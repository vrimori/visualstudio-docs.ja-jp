---
title: "単一および複数のタブ ビュー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] カスタム - 単一および複数のタブ ビュー"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 単一および複数のタブ ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターはビューの作成できます。  1 番目の例ではコード エディター ウィンドウ別のフォームです。  
  
 複数のタブにフォーカスを移動したビューは複数のタブがあるビューです。  たとえばHTML エディターに下に 2 個のタブがあります : 各  **デザイン**  と  **ソース**  論理ビュー。  デザイン ビューではは Web ページを構成する HTML が表示されますがレンダリングされる Web ページが表示されます。  
  
## 物理ビューのアクセス  
 物理ホスト ビューのドキュメントのビュー オブジェクトコードやフォームのようなバッファーのデータのビューを表すされます。  したがって各ドキュメントのビュー オブジェクトに物理ビュー \(物理ビューの文字列と呼ばれるものによって識別される\)および共通に一つの論理ビューがあります。  
  
 場合によっては物理ビューは複数の論理ビューを持つことができますが。  これには side\-by\-side の分割ウィンドウのビューを持つや GUI\/design のビューとコードの分離フォームのビューを持つフォーム エディターです。  
  
 使用可能な物理ビュー エディターのすべてにアクセスできるようにするためにエディターのファクトリを作成できるドキュメントのビュー オブジェクトの種類に固有の物理ビューの文字列を作成する必要があります。  たとえば[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ファクトリはコード エディター ウィンドウとフォーム デザイナー ウィンドウのドキュメントのビュー オブジェクトを作成できます。  
  
## 複数のタブにフォーカスを移動したビューの作成  
 さまざまな方法でデータの表示を有効にするには物理ビュー内の複数のタブを配置できますがドキュメントのビュー オブジェクトは一意の物理ビューの文字列を使用して物理ビューに関連付けられている必要があります。  この複数のタブにフォーカスを移動した構成ではすべてのタブが同じ物理ビューの文字列が関連付けられますが各タブは個別の論理ビューの GUID を指定します。  
  
 エディターの複数のタブにフォーカスを移動したビューを作成するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> のインターフェイスを実装し作成した各タブに別の論理ビューの GUID \(<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) を関連付けます。  
  
 Visual Studio HTML エディターは複数のタブ ビュー エディターの例です。  これに  **デザイン**  と  **ソース**  のタブがあります。  これを実現するには別の論理ビューは ENT0ENT \[入力\] タブの \[タブ `LOGICALVIEWID_TextView`および ENT1ENT \[入力\] タブの `LOGICALVIEWID_Code` に関連付けられます。  
  
 適切な論理ビューを指定することでVSPackageフォームコードの編集デバッグ コードの設計図のような特定の目的に対応するビューにアクセスできます。  ただしウィンドウの 1 つが null 文字列で指定されていない場合主要な論理ビュー \(\)`LOGVIEWID_Primary` に対応する必要があります。  
  
 次の表は使用可能な論理ビューの値としてを示します。  
  
|LOGVIEWID の GUID|推奨される使用法|  
|----------------------|--------------|  
|`LOGVIEWID_Primary`|エディターのファクトリの既定値と主要なビューです。<br /><br /> すべてのエディターのファクトリはこの値をサポートする必要があります。  このビューは物理ビューの null 文字列を使用する必要があります。  1 文字以上の論理ビューはこの値を設定する必要があります。|  
|`LOGVIEWID_Debugging`|ビューをデバッグします。  通常同じへの `LOGVIEWID_Debugging` のマップは `LOGVIEWID_Code` として表示されます。|  
|`LOGVIEWID_Code`|**コードの表示**  のコマンドで開始されます。|  
|`LOGVIEWID_Designer`|**\*\*\* View Form \*\*\*** のコマンドで開始されます。|  
|`LOGVIEWID_TextView`|テキスト エディター ビュー。  これは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> にアクセスできる <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> を返すビューです。|  
|`LOGVIEWID_UserChooseView`|ユーザーが選択できるように求められます使用するように表示できます。|  
|`LOGVIEWID_ProjectSpecificEditor`|\[出力\] ダイアログ ボックスに ENT0ENT を渡す<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> ユーザーが \[プロジェクトの既定値エディター \(\) 」エントリを選択します。|  
  
 論理ビューの GUID は拡張可能ですがVSPackage で定義された論理ビューの GUID のみ使用できます。  
  
 シャットダウンではVisual Studio がソリューションを開き直すとドキュメント ウィンドウを再開するためにドキュメント ウィンドウに関連付けられているエディターのファクトリと物理ビューの文字列 GUID を保持します。  ソリューションが終了したときに現在開いているペインのみのソリューション ファイル \(.suo\) に保持されます。  これらの値は <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> のメソッドの `propid` のパラメーターで渡される `VSFPROPID_guidEditorType` と `VSFPROPID_pszPhysicalView` の値に対応します。  
  
## 例  
 このスニペットはビューへのアクセスに <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> のオブジェクトが実装 `IVsCodeWindow` どのように使用されるかについて説明します。  この場合ウィンドウ フレームへのポインターを取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> サービスが <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> を呼び出し`LOGVIEWID_TextView` を要求するために使用されます。  ドキュメントのビュー オブジェクトへのポインターを <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> を呼び出し`VSFPROPID_DocView` の値を指定することになります。  ドキュメントのビュー オブジェクトから`QueryInterface` は `IVsCodeWindow` に対して呼び出されます。  この場合はテキスト エディターですが返されるため <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> のメソッドに返されるドキュメントのビュー オブジェクトはコード ウィンドウです。  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## 参照  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [方法: データを文書化するビューのアタッチ](../extensibility/how-to-attach-views-to-document-data.md)   
 [カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md)