---
title: "ポートのサプライヤー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41c797d2c04c630d5aee7ff5ca2c0d5fc084026a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="port-suppliers"></a>ポートの仕入先
デバッガーのアーキテクチャの観点から、**ポート サプライヤー**:  
  
-   サーバーが含まれてし、そのサーバーへの要求でポートを提供します。  
  
-   追加し、ポートを含む、サーバーから削除できます。  
  
-   サーバーに渡すことがすべてのポートを列挙できます。  
  
-   によって表される、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)レジストリを使用して Visual Studio で登録されているインターフェイス。 このインターフェイスを呼び出すことによって取得できます[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既定のポートの仕入先と、既定のポートを提供します。 カスタム ポートを実装する場合は、カスタム ポート業者も実装する必要がそれらのカスタム ポートを指定します。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [ポート](../../extensibility/debugger/ports.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)