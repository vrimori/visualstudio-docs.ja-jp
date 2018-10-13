---
title: 1 つと複数タブのビュー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e429add1b4b18cff84a2933601c56c7b026db15
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236003"
---
# <a name="single-and-multi-tab-views"></a>単一タブと複数タブのビュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディターでは、さまざまな種類のビューを作成できます。 1 つの例は、コード エディター ウィンドウで、もう 1 つは、フォーム デザイナー。  
  
 マルチタブのビューは、複数のタブのあるビューです。 たとえば、2 つのタブの下部に HTML エディター:**デザイン**と**ソース**、それぞれ論理ビューが表示されます。 デザイン ビューでは、web ページを構成する HTML が表示されます、他に、表示された web ページが表示されます。  
  
## <a name="accessing-physical-views"></a>物理ビューへのアクセス  
 物理ビューは、コードやフォームなど、バッファー内のデータのビューを表す各ドキュメント ビュー オブジェクトをホストします。 したがって、各ドキュメント ビュー オブジェクトは、(物理ビューが表示文字列と呼ばれるものによって識別される) 物理ビュー、および一般的に 1 つの論理ビューをが。  
  
 場合によっては、ただし、物理ビューで保持できる 2 つ以上の論理ビュー。 いくつかの例とサイド バイ サイドでのビュー、分割ウィンドウのエディターまたは GUI/デザイン ビューとコードの分離--フォーム ビューを持つフォーム デザイナーです。  
  
 使用可能な物理ビューのすべてにアクセスする、エディターを有効にするには、エディター ファクトリを作成できるドキュメント ビュー オブジェクトの種類ごとに一意の物理的な表示文字列を作成する必要があります。 たとえば、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]エディター ファクトリ作成ドキュメント コード ウィンドウ、フォーム デザイナー ウィンドウのオブジェクトを表示できます。  
  
## <a name="creating-multi-tabbed-views"></a>マルチタブのビューを作成します。  
 ドキュメント ビュー オブジェクトは、一意の物理的な表示文字列を使用して、物理ビューを関連付ける必要がある、ただし、さまざまな方法でデータの表示を有効にする物理ビュー内の複数のタブを配置できます。 このマルチタブの構成ですべてのタブは、同じ物理ビューが表示文字列に関連付けられますが、各タブには、別の論理ビュー GUID が与えられます。  
  
 エディターの複数のタブのビューを作成するには、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>インターフェイスし、別の論理ビュー GUID を関連付ける (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) を作成する各タブにします。  
  
 Visual Studio の HTML エディターは、複数のタブ ビューを使用して、エディターの例を示します。 **デザイン**と**ソース**タブ。 これを有効にする別の論理ビューは、各タブでは、関連付けられている`LOGICALVIEWID_TextView`の**デザイン** タブと`LOGICALVIEWID_Code`の**ソース**タブ。  
  
 適切な論理ビューを指定すると、フォームのデザイン、コードの編集、コードのデバッグなどの特定の目的に対応するビューを VSPackage にアクセスできます。 ただし、NULL 文字列で、windows のいずれかを識別する必要があります、これは、プライマリの論理ビューに対応する必要があります (`LOGVIEWID_Primary`)。  
  
 次の表は、使用可能な論理ビューの値とその使用を示します。  
  
|LOGVIEWID GUID|推奨される使用|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|エディター ファクトリの既定/プライマリ ビュー。<br /><br /> すべてのエディター ファクトリは、この値をサポートする必要があります。 このビューでは、その物理ビュー文字列として、NULL 文字列を使用する必要があります。 少なくとも 1 つの論理ビューは、この値に設定する必要があります。|  
|`LOGVIEWID_Debugging`|ビューをデバッグします。 通常、`LOGVIEWID_Debugging`として同じビューに対応する`LOGVIEWID_Code`します。|  
|`LOGVIEWID_Code`|ビューが起動して、**コードの表示**コマンド。|  
|`LOGVIEWID_Designer`|ビューが起動して、**ビュー フォーム**コマンド。|  
|`LOGVIEWID_TextView`|テキスト エディターのビュー。 これは、ビューを返す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>からアクセスできる<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。|  
|`LOGVIEWID_UserChooseView`|使用するビューを選択するユーザーに求めます。|  
|`LOGVIEWID_ProjectSpecificEditor`|によって渡される、**プログラムから開く** ダイアログ ボックス<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> ときに、ユーザーは、「(プロジェクトの既定エディター)」のエントリを選択します。|  
  
 論理ビューの Guid は拡張可能な VSPackage で定義されている論理ビューの Guid のみを使用できます。  
  
 シャット ダウン時、Visual Studio には、ソリューションを再度開いたときに、ドキュメント ウィンドウを開き直すために使用できるように、ドキュメント ウィンドウに関連付けられている文字列の物理的な表示エディター ファクトリの GUID が保持されます。 ソリューションが閉じられたときに開いているウィンドウのみが、ソリューション (.suo) ファイルに保存されます。 これらの値に対応して、`VSFPROPID_guidEditorType`と`VSFPROPID_pszPhysicalView`で渡される値、`propid`パラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッド。  
  
## <a name="example"></a>例  
 このスニペットを示していますが、どのように<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>オブジェクトが実装するビューにアクセスするために使用`IVsCodeWindow`します。 ここで、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>サービス呼び出しを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>と要求`LOGVIEWID_TextView`、ウィンドウ フレームへのポインターを取得します。 ドキュメント ビューのオブジェクトへのポインターが呼び出すことによって取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>の値を指定して`VSFPROPID_DocView`します。 ドキュメント ビュー オブジェクトから`QueryInterface`が呼び出されると`IVsCodeWindow`します。 期待は、テキスト エディターが返されで、ドキュメント ビュー オブジェクトが返されるためにここでは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッドはコード ウィンドウです。  
  
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
  
## <a name="see-also"></a>関連項目  
 [複数のドキュメント ビューのサポート](../extensibility/supporting-multiple-document-views.md)   
 [方法: ビュー ドキュメント データへのアタッチ](../extensibility/how-to-attach-views-to-document-data.md)   
 [カスタム エディターとデザイナーの作成](../extensibility/creating-custom-editors-and-designers.md)

