---
title: ポート サプライヤー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3be95dfdb84f373730d087e9d6da1096891770af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540113"
---
# <a name="port-suppliers"></a>ポート サプライヤー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ポート サプライヤー](https://docs.microsoft.com/visualstudio/extensibility/debugger/port-suppliers)します。  
  
デバッガーのアーキテクチャの観点から、**ポート サプライヤー**:  
  
-   サーバーに含まれていて、そのサーバーへの要求でポートを提供します。  
  
-   追加し、ポートを含む、サーバーから削除できます。  
  
-   これがサーバーに提供されているすべてのポートを列挙できます。  
  
-   によって表される、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイスをレジストリを使用して Visual Studio に登録します。 このインターフェイスを呼び出すことによって取得できる[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 既定のポート サプライヤーと既定のポートを提供します。 カスタム ポートを実装する場合は、実装して、これらのカスタム ポートを指定することも、カスタム ポート サプライヤー必要があります。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [ポート](../../extensibility/debugger/ports.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

