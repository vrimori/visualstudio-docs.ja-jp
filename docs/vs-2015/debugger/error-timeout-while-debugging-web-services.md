---
title: エラー Web サービスのデバッグ中にタイムアウトしました |。Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544321"
---
# <a name="error-timeout-while-debugging-web-services"></a>エラー ： Web サービスのデバッグ中にタイムアウトになりました。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: Timeout While Debugging Web Services](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services)します。  
  
呼び出し元のコードから XML Web サービスにステップ インしている場合は、呼び出しがタイムアウトになってデバッグを継続できなくなることがあります。 この場合は、次のエラー メッセージが表示されます。  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>ソリューション  
 この問題を回避するには、次の例で示すように、XML Web サービス呼び出しのタイムアウト値を無限に設定します。  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



