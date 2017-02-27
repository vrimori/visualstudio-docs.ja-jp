---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "IDebugCustomViewer インターフェイス"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは形式が必要 \(EE\) な属性値を表示するには式エバリュエーターができます。  
  
## 構文  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## 実装についてのメモ  
 EE ではカスタム書式の属性値を表示するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 COM `CoCreateInstance` の関数を呼び出してこのインターフェイスのインスタンスを作成します。  `CoCreateInstance` に渡される `CLSID` はレジストリから派生します。  [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) の呼び出しはレジストリの位置を取得します。  詳細および例については" 解説 " を参照してください。  
  
## Vtable の順序でメソッド  
 このインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[値](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|指定された値の表示に必要な数とは関係なくします。|  
  
## 解説  
 このインターフェイスには属性値がデータ テーブルなどの複雑なプロパティ型の例は規格によって表示できない場合に使用されます。  `IDebugCustomViewer` のインターフェイスで表されるするカスタム ビューアーはEE に関係なく特定の種類のデータを表示するための外部プログラムである型のビジュアライザーが異なる場合があります。  EE はEE に固有のカスタム ビューアーを実行します。  型のビジュアライザーまたはカスタム ビューアーに応じて使用するビジュアライザーのユーザー型を選択します。  手順の詳細については [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md) を参照してください。  
  
 したがってカスタム ビューアーは EE と同じ方法で登録されGUID と言語の販売元の GUID が必要です。  正確なメトリック \(またはレジストリ エントリの名前 EE にのみ\) と呼ばれます。  このメトリックは [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) の呼び出しによって返される [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) の構造体にを返します。  COM `CoCreateInstance` 関数に渡されるメトリックスの値を `CLSID` です \(例を参照\)。  
  
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) の関数`SetEEMetric` がカスタム ビューアーを登録するために使用できます。  特定のレジストリ キーについては 「」 `Debugging SDK Helpers` の式エバリュエーターのレジストリのセクションをカスタム ビューアーの要件 " " を参照してください。  カスタム ビューアーは式エバリュエーターが複数の定義済みのメトリックを必要とする場合 \(EE の実装によって定義されている1\) で実現できることに注意してください。  
  
 通常はカスタム ビューアーは [値](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) に指定された [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) のインターフェイスに文字列として以外のプロパティ値を変更するためのメソッドがないためデータの読み取り専用のビューを提供します。  データの任意のブロックの変更をサポートするにはEE同じオブジェクトのカスタム インターフェイスを実装する `IDebugProperty3` のインターフェイスを実装します。  このカスタム インターフェイスはデータの任意のブロックを変更するために必要なメソッドを提供します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 使用例  
 そのプロパティにカスタム ビューアーの場合この例ではプロパティから最初のカスタム ビューアーを取得する方法を示します。  
  
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
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)