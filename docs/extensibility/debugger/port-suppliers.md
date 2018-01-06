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
ms.workload: vssdk
ms.openlocfilehash: 0cab184b0ecf4c4971b116cc9dfde26d8f80b45f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="port-suppliers"></a>ポートの仕入先
デバッガーのアーキテクチャの観点から、**ポート サプライヤー**:  
  
-   サーバーが含まれてし、そのサーバーへの要求でポートを提供します。  
  
-   追加し、ポートを含む、サーバーから削除できます。  
  
-   サーバーに渡すことがすべてのポートを列挙できます。  
  
-   によって表される、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)レジストリを使用して Visual Studio で登録されているインターフェイス。 このインターフェイスを呼び出すことによって取得できます[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既定のポートの仕入先と、既定のポートを提供します。 カスタム ポートを実装する場合は、カスタム ポート業者も実装する必要がそれらのカスタム ポートを指定します。  
  
## <a name="see-also"></a>参照  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [ポート](../../extensibility/debugger/ports.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)