---
title: 'エラー: IP アドレスを使用するサイト |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c97d9eb715711b3315c97a95503489b87f323f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-site-uses-ip-address"></a>エラー : サイトは IP アドレスを使用しています
このエラーは、IP アドレスを使用している Web アプリケーションに、デバッガーが自動アタッチしようとしたときに発生します。 これを変更する場合に発生**Web サイトの識別**に**特定の IP アドレスを使用して**IIS でします。  
  
 自動アタッチが機能するには、コンピューター名だけでなく、IP アドレスを指定したプロジェクトを作成する必要があります。 そうしないと、コンピューター名は localhost に変更されるため、DEBUG 動詞を IIS に送信するときにエラーが発生します。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  使用する手動のアタッチ (デバッグ メニューから選択**プロセスにアタッチする**)。  
  
     または  
  
2.  変更、 **IIS Web サイトの識別**設定します。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)