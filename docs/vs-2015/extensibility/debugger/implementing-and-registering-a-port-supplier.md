---
title: 実装して、ポートのサプライヤーの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3844d6beca76781f741bfbe0c6bff71923075d36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728936"
---
# <a name="implementing-and-registering-a-port-supplier"></a>ポート サプライヤーの実装および登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ポート サプライヤーの役割は、追跡し、さらにプロセスの管理のポートを指定することです。 ポート サプライヤーは、ポートを作成する必要がある時に、(セッション デバッグ マネージャー [SDM] は、ユーザーが選択したポート サプライヤーまたはプロジェクト システムによって指定されたポート サプライヤーに使用されます) のポート サプライヤーの GUID を持つ CoCreate を使用してインスタンス化されます。 SDM を呼び出して[CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)を任意のポートを追加できるかどうかを参照してください。 呼び出すことによって、新しいポートが要求されたポートを追加できる場合[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)を渡す、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)ポートをについて説明します。 `AddPort` によって表される新しいポートを返す、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイス。  
  
## <a name="discussion"></a>説明  
 ポートは、さらに、マシンまたはデバッグ サーバーと関連付けられているポートのサプライヤーによって作成されます。 サーバーからそのポート サプライヤーを列挙できる、[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)を介してそのポートを列挙できるメソッド、およびポート サプライヤー、 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)メソッド。  
  
 通常の COM 登録に加えてポート サプライヤーする必要がありますの登録に Visual Studio の CLSID、名前を特定のレジストリの場所に配置することで。 Debugging SDK ヘルパー関数を呼び出す`SetMetric`この雑務を処理します。 そのため、登録するには、各項目に対して 1 回呼び出されます。  
  
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
  
 ポート サプライヤーは呼び出すことで登録解除`RemoveMetric`(別の SDK のデバッグ ヘルパー関数) ため、登録された各項目に対して 1 回。  
  
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
>  [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric`と`RemoveMetric`は静的関数 dbgmetric.h で定義され、ad2de.lib にコンパイルします。 `metrictypePortSupplier`、 `metricCLSID`、および`metricName`ヘルパーも dbgmetric.h で定義されます。  
  
 ポート サプライヤーは、メソッドの名前と GUID を指定できます[GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)と[GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)、それぞれします。  
  
## <a name="see-also"></a>関連項目  
 [ポート サプライヤーの実装](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)

