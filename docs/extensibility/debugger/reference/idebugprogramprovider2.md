---
title: "IDebugProgramProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2"
helpviewer_keywords: 
  - "IDebugProgramProvider2 インターフェイス"
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

登録されたインターフェイスはデバッグ セッションの管理に \(SDM\) [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) のインターフェイスを通じて 「発行された」プログラムに関する情報を取得できるようにします。  
  
## 構文  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンで\(DE\) プログラムに関する情報を提供するにはこのインターフェイスを実装します。  このインターフェイスは [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) に説明されているように非常 `metricProgramProvider` を使用してレジストリの de\-DE のセクションに登録します。  
  
## 呼び出し元のメモ  
 レジストリから派生したプログラムのプロバイダーの `CLSID` の呼び出しの COM `CoCreateInstance` の関数。  例を参照してください。  
  
## Vtable の順序でメソッド  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|さまざまな方法でフィルター処理プログラムの実行に関する情報を取得します。|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|特定のプロセス ID を持つプログラムのノードを取得します|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|コールバックを特定の種類のプロセスに関連付けられたプロバイダーのイベントを表示するに設定します。|  
|[Setlocale 関数](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|DE に必要な言語固有のリソースのロケールを設定します。|  
  
## 解説  
 通常プロセスはそのプロセスで実行するプログラムについて調べるにはこのインターフェイスを使用します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 使用例  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)