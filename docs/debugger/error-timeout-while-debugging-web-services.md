---
title: 'エラー: Web サービスのデバッグ中にタイムアウトしました |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d095278ca684d8e2f6bc5b2e764b997ed88b7d33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-timeout-while-debugging-web-services"></a>エラー ： Web サービスのデバッグ中にタイムアウトになりました。
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