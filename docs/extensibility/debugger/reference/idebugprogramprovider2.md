---
title: IDebugProgramProvider2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6fca410ed773b2a062623465c78942484c692f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857346"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
登録されているこのインターフェイスにより、セッション デバッグ マネージャー (SDM) が公開されている""を通じてプログラムに関する情報を取得、 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)インターフェイス。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、デバッグ中のプログラムに関する情報を提供するには、このインターフェイスを実装します。 このインターフェイスは、メトリックを使用して、レジストリの DE セクションに登録されている`metricProgramProvider`」の説明に従って、[デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 COM の呼び出し`CoCreateInstance`関数と、`CLSID`のレジストリから取得したプログラムの提供。 例を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|プログラムを実行している、さまざまな方法でフィルター処理に関する情報を取得します。|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|特定のプロセス ID が指定された、[プログラム] ノードを取得します|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|プロセスの特定の種類に関連付けられているプロバイダーのイベントをウォッチするコールバックを確立します。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|DE で必要なすべての言語固有リソースのロケールを確立します。|  
  
## <a name="remarks"></a>Remarks  
 通常、プロセスはこのインターフェイスを使用して、そのプロセスで実行されているプログラムについて説明します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
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
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)