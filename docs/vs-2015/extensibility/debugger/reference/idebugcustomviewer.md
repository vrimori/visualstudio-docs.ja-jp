---
title: IDebugCustomViewer |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 814bf0b43d217f3309e50c54db70bef850e6ed50
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257583"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、式エバリュエーターでどのような形式は必要なプロパティの値を表示するには、(EE) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 EE は、カスタム形式でプロパティの値を表示するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 COM の呼び出し`CoCreateInstance`関数は、このインターフェイスをインスタンス化します。 `CLSID`に渡される`CoCreateInstance`レジストリから取得されます。 呼び出し[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)レジストリの場所を取得します。 詳細と例では、「解説」を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|指定された値を表示するために必要なことすべてを実行します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティの値は、通常の方法で表示できない場合、このインターフェイスを使用: などのデータ テーブルまたは別の複合プロパティの型。 によって表されるとしてのカスタム ビューアー、`IDebugCustomViewer`インターフェイス、EE に関係なく、特定の種類のデータを表示するための外部のプログラムである型のビジュアライザーとは異なります。 EE は、その EE に固有のカスタム ビューアーを実装します。 ユーザーは、型のビジュアライザーやカスタム ビューアーを使用するビジュアライザーの種類を選択します。 参照してください[視覚化してデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)このプロセスの詳細について。  
  
 カスタム ビューアーは、EE と同じ方法で登録され、そのため、言語の GUID と仕入先の GUID が必要です。 正確なメトリック (またはレジストリ エントリ名) は、EE にだけ呼ばれます。 このメトリックが返されます、 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 、構造体への呼び出しによって返される順番[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)します。 メトリックに格納されている値は、 `CLSID` COM に渡される`CoCreateInstance`関数 (例を参照してください)。  
  
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)関数、 `SetEEMetric`、カスタム ビューアーの登録に使用することができます。 「の式エバリュエーター」レジストリ セクションを参照してください。`Debugging SDK Helpers`特定のレジストリ キーのカスタム ビューアー必要があります。 カスタム ビューアーでは、式エバリュエーターには、いくつかの定義済みのメトリックが必要ですが、(EE の実装者が定義されます) を 1 つだけのメトリックが必要があることに注意してください。  
  
 通常、データの読み取り専用ビューは、カスタム ビューアーのため、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)に指定されたインターフェイス[値](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)以外を文字列としてのプロパティの値を変更するためのメソッドがありません。 データの任意のブロックの変更をサポートするために、EE を実装する同一のオブジェクトにカスタム インターフェイスを実装して、`IDebugProperty3`インターフェイス。 このカスタム インターフェイスは、データの任意のブロックを変更するために必要なメソッドを提供しは。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、そのプロパティに任意のカスタム ビューアーがある場合、最初のカスタム ビューアーをプロパティから取得する方法を示します。  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

