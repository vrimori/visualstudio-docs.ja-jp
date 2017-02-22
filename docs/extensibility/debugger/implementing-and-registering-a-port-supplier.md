---
title: "実装して、ポート サプライヤーを登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] のデバッグ、ポート サプライヤーを登録します。"
  - "ポートの供給業者、登録します。"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 実装して、ポート サプライヤーを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ポートのサプライヤーのロールはプロセスを管理する追跡し提供ポートです。  実行時にポートを作成する必要があるポートの業者はポートのサプライヤーの GUID に CoCreate を使用してインスタンス化されます \(セッションはプロジェクト システムによってマネージャー SDM \[入力\] ポートのサプライヤー選択したユーザーまたはポートの業者を使用するデバッグ指定します\)。  SDM はポートを追加できるかどうかを [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) を呼び出します。  ポートを追加できる場合は新しいポートは [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) を呼び出しポートを記述することに [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) を渡して要求されます。  `AddPort` は [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) のインターフェイスが表す新しいポートを返します。  
  
## 説明  
 ポートはマシン レベルまたはデバッグ Server と関連付けられているポートの仕入先によって作成されます。  サーバーは [EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) のメソッドによってポートの業者を列挙ポートの業者は [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) のメソッドでポートを列挙できます。  
  
 一般的な COM 登録に加えてポートの業者は特定のレジストリの位置CLSID と名前を指定することでVisual Studio に登録する必要があります。  デバッグ SDK のヘルパー関数は `SetMetric` ハンドルをこの雑用という : したがって登録する項目に一度だけ呼び出されます :  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 このポートのサプライヤー登録された項目ごとに個別のデバッガー `RemoveMetric` \(SDK\) のヘルパー関数を一度呼び出すことにより独自の登録を解除します :  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` と `RemoveMetric` は dbgmetric.h で定義されad2de.lib にコンパイルされた静的関数です。  `metrictypePortSupplier``metricCLSID` と `metricName` ヘルパーはdbgmetric.h で定義されます。  
  
 ポートの業者はメソッド [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) と [GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md) によってそれぞれ名前と GUID を指定できます。  
  
## 参照  
 [ポートのサプライヤーを実装します。](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [ポートの仕入先](../../extensibility/debugger/port-suppliers.md)