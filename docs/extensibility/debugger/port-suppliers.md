---
title: ポート サプライヤー |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5385e006bcd2f79ab7b1c2e723e696b833991f36
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252350"
---
# <a name="port-suppliers"></a>ポート サプライヤー
デバッガーのアーキテクチャで、*ポート サプライヤー*:  
  
-   サーバーに含まれていて、そのサーバーへの要求でポートを提供します。  
  
-   追加し、ポートを含む、サーバーから削除できます。  
  
-   これがサーバーに提供されているすべてのポートを列挙できます。  
  
-   によって表される、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイスをレジストリを使用して Visual Studio に登録します。 このインターフェイスを呼び出すことによって取得できる[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 既定のポート サプライヤーと既定のポートを提供します。 カスタム ポートを実装する場合は、実装して、これらのカスタム ポートを指定することも、カスタム ポート サプライヤー必要があります。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [ポート](../../extensibility/debugger/ports.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)