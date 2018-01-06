---
title: "実装して、ポートのサプライヤーの登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c05dc0bd15dc5c1959024327396d848cd0b1112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>実装して、ポートのサプライヤーの登録
ポートのサプライヤーの役割は、追跡し、さらにプロセスの管理のポートを指定します。 ポートを作成する必要がある時点で、(ポート仕入先ユーザーが選択したか、プロジェクト システムによって指定されたポート サプライヤーは、セッション デバッグ マネージャー [SDM] を使用して)、ポート業者の GUID を持つ CoCreate を使用して、ポート業者がインスタンス化されます。 次に呼び出されます、SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)を表示するかどうかは、任意のポートを追加できます。 呼び出して、新しいポートが要求された場合は、ポートを追加することができます、 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)を渡すこと、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)ポートをについて説明します。 `AddPort`によって表される新しいポートを返す、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイスです。  
  
## <a name="discussion"></a>説明  
 さらに、コンピューターまたはデバッグ サーバーに関連付けられているポート業者によってポートが作成されます。 サーバーがそのポート サプライヤーを通じてを列挙できます、[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)メソッド、およびポート サプライヤーは、使用して、そのポートを列挙できます、 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)メソッドです。  
  
 通常の COM 登録に加えてポート サプライヤー登録する必要があります自体 Visual Studio で、CLSID、名前を特定のレジストリの場所に配置することによってです。 Debugging SDK ヘルパー関数を呼び出す`SetMetric`この面倒な作業を処理します。 したがって、登録するには、各項目に対して 1 回呼び出されます。  
  
```cpp  
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
  
 ポートの供給業者は呼び出すことで登録解除`RemoveMetric`(別の SDK のデバッグ ヘルパー関数) ため、登録されている項目ごとに 1 回。  
  
```cpp  
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
>  [をデバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric`と`RemoveMetric`dbgmetric.h で定義され、ad2de.lib にコンパイルされた関数が静的です。 `metrictypePortSupplier`、 `metricCLSID`、および`metricName`ヘルパー dbgmetric.h に定義されています。  
  
 ポート サプライヤー メソッドによって、名前と GUID を提供できる[GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)と[GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)、それぞれします。  
  
## <a name="see-also"></a>参照  
 [ポートのサプライヤーを実装します。](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)