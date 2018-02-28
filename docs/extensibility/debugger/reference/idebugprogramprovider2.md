---
title: "IDebugProgramProvider2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 37771a5ea9f35075200cd5d5309bc5836afd11bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
登録されたこのインターフェイスにより、セッションのデバッグ manager「公開済み」からのプログラムに関する情報を取得するには、(SDM)、 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、デバッグ中のプログラムに関する情報を提供するには、このインターフェイスを実装します。 このインターフェイスは、セクションに登録されて、DE、メトリックを使用して、レジストリの`metricProgramProvider`」の説明に従って、[をデバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 COM の呼び出し`CoCreateInstance`で機能、`CLSID`のレジストリから取得されるプログラムの提供します。 この例を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|プログラムを実行している、さまざまな方法でフィルター処理の情報を取得します。|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|特定のプロセス ID が指定された、[プログラム] ノードを取得します。|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|特定の種類のプロセスに関連付けられているプロバイダーのイベントを監視するコールバックを設定します。|  
|[Setlocale、_wsetlocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|言語固有のリソースが、DE で必要な任意のロケールを設定します。|  
  
## <a name="remarks"></a>コメント  
 通常、プロセスは、そのプロセスで実行されているプログラムについてこのインターフェイスを使用します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
  
```cpp  
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
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)