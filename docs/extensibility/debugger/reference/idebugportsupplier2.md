---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "IDebugPortSupplier2 インターフェイス"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

セッションにこのインターフェイスの提供ポートはマネージャーを \(SDM\) デバッグします。  
  
## 構文  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者はポートの業者を表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 ポートの仕入先 `GUID` の `CoCreateInstance` の呼び出しはこのインターフェイスを返します \(これはこのインターフェイスを取得する一般的な方法です。  次に例を示します。  
  
```cpp#  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) の呼び出しは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] で使用されている現在のポートの業者を表すこのインターフェイスを返します。  
  
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md) はポートを作成したポートの業者を表すこのインターフェイスを返します。  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) は `IDebugPortSupplier` のインターフェイスの一覧を表します \(`IEnumDebugPortSuppliers` のインターフェイスは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] に登録されたポートのサプライヤーすべてを表す [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) から派生します\)。  
  
 デバッグ エンジンはポートのサプライヤーと相互に対話しません。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPortSupplier2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|ポートのサプライヤーの名前を取得します。|  
|[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)|ポートのサプライヤーの識別子を取得します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|ポートのサプライヤーからポートを取得します。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|既存のポートを列挙します。|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|ポートのサプライヤーが新しいポートの追加をサポートしていることを確認します。|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|ポートを追加します。|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|ポートを削除します。|  
  
## 解説  
 ポートの業者はその ID を名前で指定して追加しポートを削除しポートのサプライヤーが提供するすべてのポートを列挙できます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)