---
title: サーバー (Visual Studio SDK) |Microsoft Docs
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
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549116"
---
# <a name="servers-visual-studio-sdk"></a>サーバー (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サーバー (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk)します。  
  
デバッガーのアーキテクチャの観点から、 **server**:  
  
-   ポートおよびポート サプライヤーのコンテナーは、セッション デバッグ マネージャー (SDM) のポートとポート サプライヤーの通信し、エンジンのデバッグに使用されます。  
  
-   名前で識別し、そのポートとポート サプライヤーを列挙できます。  
  
-   によって表される、 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)インターフェイスで、Visual Studio (Visual Studio の実行の各インスタンスのサーバーの 1 つのインスタンス) によってのみ実装されます。  
  
## <a name="see-also"></a>関連項目  
 [ポート](../../extensibility/debugger/ports.md)   
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

