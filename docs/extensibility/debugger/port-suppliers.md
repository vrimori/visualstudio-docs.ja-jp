---
title: ポート サプライヤー |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e134b9b4adeb45693a9841a0a867a9c3630bf2aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835105"
---
# <a name="port-suppliers"></a>ポート サプライヤー
デバッガーのアーキテクチャで、*ポート サプライヤー*:  
  
- サーバーに含まれていて、そのサーバーへの要求でポートを提供します。  
  
- 追加し、ポートを含む、サーバーから削除できます。  
  
- これがサーバーに提供されているすべてのポートを列挙できます。  
  
- によって表される、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイスをレジストリを使用して Visual Studio に登録します。 このインターフェイスを呼び出すことによって取得できる[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)します。  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 既定のポート サプライヤーと既定のポートを提供します。 カスタム ポートを実装する場合は、実装して、これらのカスタム ポートを指定することも、カスタム ポート サプライヤー必要があります。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [ポート](../../extensibility/debugger/ports.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)