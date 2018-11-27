---
title: サーバー (Visual Studio SDK) |Microsoft Docs
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
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20b1550773be903f3f5a0482d2971a4f5b30fabc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727144"
---
# <a name="servers-visual-studio-sdk"></a>サーバー (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッガーのアーキテクチャの観点から、 **server**:  
  
-   ポートおよびポート サプライヤーのコンテナーは、セッション デバッグ マネージャー (SDM) のポートとポート サプライヤーの通信し、エンジンのデバッグに使用されます。  
  
-   名前で識別し、そのポートとポート サプライヤーを列挙できます。  
  
-   によって表される、 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイスで、Visual Studio (Visual Studio の実行の各インスタンスのサーバーの 1 つのインスタンス) によってのみ実装されます。  
  
## <a name="see-also"></a>関連項目  
 [ポート](../../extensibility/debugger/ports.md)   
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

