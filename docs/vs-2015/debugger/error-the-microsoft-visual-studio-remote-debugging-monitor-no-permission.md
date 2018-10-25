---
title: 'エラー: Microsoft Visual Studio リモート デバッグ モニター、リモート コンピューター上にこのコンピューターに接続する権限がありません |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20accedd9591c777cad26aed30c05954dfabbdfc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811090"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>エラー : リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターには、このコンピューターに接続するアクセス許可がありません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このエラーは、Visual Studio リモート デバッグ モニター (msvsmon) を実行しようとしたユーザーのアカウントがローカル コンピューターにない場合に発生します。  
  
### <a name="to-fix-this-problem"></a>この問題を解決するには  
  
- リモート コンピューターで msvsmon を実行しているユーザー アカウントと同じ名前およびパスワードを使用して、Visual Studio デバッガー ホスト コンピューターにユーザー アカウントを追加します。  
  
   \- または -  
  
- ローカル コンピューターを呼び出すアクセス許可を持つユーザーとして msvsmon を実行します。 つまり、ユーザーは msvsmon コンピューターのドメイン ユーザーおよび管理者である必要があります。 msvsmon を実行するユーザー アカウントは次の 2 とおりの方法で指定できます。  
  
  - Msvsmon アイコンを右クリックし **実行**ショートカット メニューの   
  
    \- または -  
  
  - コマンド プロンプトで `runas.exe` を実行します。  
  
## <a name="see-also"></a>関連項目  
 [リモート ドメイン間でのデバッグ](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



