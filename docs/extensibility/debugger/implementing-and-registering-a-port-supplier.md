---
title: 実装して、ポートのサプライヤーの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10e68f06cde3cd562b145bd64f94581c65f7d7f6
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231647"
---
# <a name="implement-and-register-a-port-supplier"></a>実装し、ポートのサプライヤーの登録
ポート サプライヤーの役割は、追跡し、さらにプロセスの管理のポートを指定することです。 ポートを作成する場合、ポート サプライヤーは、(セッション デバッグ マネージャー [SDM] が選択されているユーザーまたはポート サプライヤーは、プロジェクト システムで指定されているポート サプライヤーで使用されます) のポート サプライヤーの GUID を持つ CoCreate を使用してインスタンス化されます。 SDM を呼び出して[CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)を任意のポートを追加できるかどうかを参照してください。 呼び出すことによって、新しいポートが要求されたポートを追加できる場合[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)を渡す、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)ポートをについて説明します。 `AddPort` によって表される新しいポートを返します、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイス。  
  
## <a name="discussion"></a>説明  
 ポートは、マシンまたはデバッグ サーバーに関連付けられたポートのサプライヤーによって作成されます。 サーバーからそのポート サプライヤーの列挙、[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)メソッド、およびポート サプライヤーを介してそのポートを列挙、 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)メソッド。  
  
 通常の COM 登録に加えてポート サプライヤーする必要がありますの登録に Visual Studio の CLSID、名前を特定のレジストリの場所に配置することで。 Debugging SDK ヘルパー関数を呼び出す`SetMetric`この雑務を処理します。 そのため、登録するには、各項目に対して 1 回呼び出されます。  
  
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
  
 ポート サプライヤーは呼び出すことで登録解除`RemoveMetric`(別の SDK のデバッグ ヘルパー関数) ため、登録された各項目に対して 1 回。  
  
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
>  [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric`と`RemoveMetric`静的関数で定義されている*dbgmetric.h*とにコンパイルされる*ad2de.lib*します。 `metrictypePortSupplier`、 `metricCLSID`、および`metricName`ヘルパーも定義*dbgmetric.h*します。  
  
 ポート サプライヤーは、メソッドの名前と GUID を指定できます[GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)と[GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)、それぞれします。  
  
## <a name="see-also"></a>関連項目  
 [ポート サプライヤーを実装します。](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)