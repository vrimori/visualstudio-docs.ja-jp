---
title: エラー Web サービスのデバッグ中にタイムアウトしました |。Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 985082d675da2a56d9880414809d91e92cb1fe0d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736347"
---
# <a name="error-timeout-while-debugging-web-services"></a>エラー ： Web サービスのデバッグ中にタイムアウトになりました。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



