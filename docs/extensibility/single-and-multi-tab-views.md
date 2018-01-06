---
title: "単一サブネットおよびマルチ タブのビュー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>単一サブネットおよびマルチ タブのビュー
エディターには、さまざまな種類のビューを作成できます。 1 つの例は、コード エディター ウィンドウ、フォーム デザイナーは別です。  
  
 複数のタブのビューは、複数のタブのあるビューです。 たとえば、HTML エディターが下部にある 2 つのタブを持つ:**デザイン**と**ソース**、各論理ビューです。 デザイン ビューでは、web ページで構成された HTML が表示されますが、他の表示された web ページが表示されます。  
  
## <a name="accessing-physical-views"></a>物理ビューへのアクセス  
 物理ビューは、それぞれが表すコードまたはフォームなど、バッファー内のデータの表示ドキュメント ビュー オブジェクトをホストします。 同様に、各ドキュメント ビュー オブジェクトは、物理的なビュー (物理的な表示文字列と呼ばれるもので識別される) と通常、1 つの論理ビューです。  
  
 場合によっては、ただし、物理ビューを持つ 2 つ以上の論理ビューあります。 いくつかの例には、サイド バイ サイドのビューでの分割ウィンドウを持つエディターまたは GUI/デザイン ビューと、コードの分離--フォーム ビューを持つフォーム デザイナーです。  
  
 アクセスの使用可能な物理ビューがすべて、エディターを有効にするには、エディター ファクトリを作成できるドキュメント ビュー オブジェクトの種類ごとに一意の物理的な表示文字列を作成する必要があります。 たとえば、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]エディター ファクトリ オブジェクトを作成できますドキュメント ビューのコード ウィンドウ、フォーム デザイナー ウィンドウです。  
  
## <a name="creating-multi-tabbed-views"></a>複数のタブのビューを作成します。  
 ドキュメント ビュー オブジェクトは、物理ビューは一意の文字列を物理ビューに関連付けられている必要があります、さまざまな方法でデータの表示を有効にする物理ビュー内の複数のタブを配置することができます。 このマルチタブの構成では、すべてのタブが、同じ物理ビュー文字列に関連付けられていますが、それぞれのタブが別の論理ビューの GUID を指定します。  
  
 エディターの複数のタブのビューを作成するには、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>インターフェイスし、別の論理ビュー GUID に関連付ける (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) を作成する各タブにします。  
  
 Visual Studio HTML エディターは、マルチ タブのビューのエディターの例を示します。 **デザイン**と**ソース**タブです。 これを有効にするを別の論理ビューがそれぞれのタブに関連付けられて`LOGICALVIEWID_TextView`の**デザイン** タブと`LOGICALVIEWID_Code`の**ソース**タブです。  
  
 適切な論理ビューを指定すると、フォームのデザイン、コードを編集またはコードのデバッグなどの特定の目的に対応するビューを VSPackage にアクセスできます。 ただし、NULL 文字列で、windows のいずれかの識別する必要があります、これは、プライマリの論理ビューに対応する必要があります (`LOGVIEWID_Primary`)。  
  
 次の表は、論理ビューを使用できる値とその使用法を示します。  
  
|LOGVIEWID GUID|推奨される使用|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|エディター ファクトリの既定/プライマリ ビュー。<br /><br /> すべてのエディター ファクトリは、この値をサポートする必要があります。 このビューでは、その物理ビュー文字列として NULL 文字列を使用する必要があります。 少なくとも 1 つの論理ビューは、この値に設定する必要があります。|  
|`LOGVIEWID_Debugging`|ビューをデバッグします。 通常、`LOGVIEWID_Debugging`として同じビューにマップ`LOGVIEWID_Code`です。|  
|`LOGVIEWID_Code`|ビューを起動、**コードの表示**コマンド。|  
|`LOGVIEWID_Designer`|ビューを起動、**フォームの表示**コマンド。|  
|`LOGVIEWID_TextView`|テキスト エディターのビュー。 これは、ビューを返す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>からアクセスできる<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。|  
|`LOGVIEWID_UserChooseView`|使用するビューを選択するユーザーに求めます。|  
|`LOGVIEWID_ProjectSpecificEditor`|によって渡される、**ファイルを開く** ダイアログ ボックス<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> ユーザーは、「(プロジェクトの既定エディター)」エントリを選択するとします。|  
  
 論理ビューの Guid は、拡張は、VSPackage で定義されている論理ビューの Guid のみを使用できます。  
  
 シャット ダウンでは、Visual Studio は、エディター ファクトリと、ソリューションを再度開いたとき、ドキュメント ウィンドウを開き直すために使用できるように、ドキュメント ウィンドウに関連付けられている物理ビュー文字列の GUID を保持します。 ソリューションが閉じられたときに開いているウィンドウのみが、ソリューション (.suo) ファイルに保存されます。 これらの値に対応して、`VSFPROPID_guidEditorType`と`VSFPROPID_pszPhysicalView`で渡される値、`propid`内のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッドです。  
  
## <a name="example"></a>例  
 この例を示していますが、どのように<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>オブジェクトを実装するビューへのアクセスに使用`IVsCodeWindow`です。 ここで、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>サービスは呼び出しに使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>と要求`LOGVIEWID_TextView`、ウィンドウ フレームへのポインターの取得元。 ドキュメント ビュー オブジェクトへのポインターが呼び出すことによって取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>の値を指定して`VSFPROPID_DocView`です。 ドキュメント ビュー オブジェクトから`QueryInterface`が呼び出されると`IVsCodeWindow`です。 ここでは、予想されますをテキスト エディターが返され、ドキュメント ビュー オブジェクト返されます。 これで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッドは、コード ウィンドウです。  
  
```cpp  
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
  
## <a name="see-also"></a>参照  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [方法: 添付ドキュメント データへのビュー](../extensibility/how-to-attach-views-to-document-data.md)   
 [カスタム エディターとデザイナーの作成](../extensibility/creating-custom-editors-and-designers.md)