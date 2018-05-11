---
title: IDebugCustomViewer |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fb70365304883abe99a87cfec5e78bbed89f2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
このインターフェイスは、式エバリュエーターにどのような形式が必要なプロパティの値を表示するには、(EE) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 EE は、カスタムの形式で、プロパティの値を表示するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 COM の呼び出し`CoCreateInstance`関数は、このインターフェイスをインスタンス化します。 `CLSID`に渡される`CoCreateInstance`レジストリから取得します。 呼び出し[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)レジストリの場所を取得します。 詳細と例では、「解説」を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスでは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[値](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|指定された値を表示するために必要なことすべてを実行します。|  
  
## <a name="remarks"></a>コメント  
 プロパティの値は、通常の方法で表示できない場合、このインターフェイスは使用-データ テーブルまたは別の複雑なプロパティの型となどです。 によって表されるとしてのカスタム ビューアー、`IDebugCustomViewer`インターフェイスでは、外部プログラムの EE に関係なく、特定の種類のデータを表示するには、型のビジュアライザーとは異なる。 EE は、その EE に固有であるカスタム ビューアーを実装します。 ユーザーは、型のビジュアライザーまたはカスタム ビューアーを使用するビジュアライザーの種類を選択します。 参照してください[Visualizing とデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)詳細についてはこのプロセスにします。  
  
 カスタム ビューアーは、EE と同じ方法で登録され、そのため、言語の GUID と仕入先の GUID が必要です。 正確なメトリック (またはレジストリ エントリ名) のみが知っている EE です。 このメトリックが返されます、 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 、構造体への呼び出しによって返される順番[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)です。 メトリックに格納されている値は、 `CLSID` COM に渡される`CoCreateInstance`関数 (例を参照してください)。  
  
 [をデバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)関数、 `SetEEMetric`、カスタム ビューアーを登録するために使用できます。 参照してください「の式エバリュエーター」レジストリの`Debugging SDK Helpers`カスタム ビューアーが必要な特定のレジストリ キーです。 カスタム ビューアーでは、式エバリュエーターには、いくつかの定義済みのメトリックが必要ですが、(EE の担当者によって定義されます) を 1 つだけのメトリックが必要があることに注意してください。  
  
 通常、カスタム ビューアーには、データの読み取り専用ビューので、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)に指定されたインターフェイス[値](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)を除く文字列としてのプロパティの値を変更する方法がありません。 任意のブロックのデータの変更をサポートするために、EE は同じオブジェクトを実装するカスタム インターフェイスを実装して、`IDebugProperty3`インターフェイスです。 このカスタム インターフェイスは、任意のデータのブロックを変更するためのメソッドになります。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、そのプロパティに任意のカスタム ビューアーがある場合、最初のカスタム ビューアーをプロパティから取得する方法を示します。  
  
```cpp  
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