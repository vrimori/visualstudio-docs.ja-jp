---
title: 'エラー: Microsoft Visual Studio リモート デバッグ モニター、リモート コンピューター上にこのコンピューターに接続する権限がありません |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 1a62f20afc5ba57da64205491a3c5dfeabd75daf
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592503"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>エラー : リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターには、このコンピューターに接続するアクセス許可がありません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: Microsoft Visual Studio リモート デバッグ モニター、リモート コンピューター上には、このコンピューターに接続する権限はありません。](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer)します。  
  
このエラーは、Visual Studio リモート デバッグ モニター (msvsmon) を実行しようとしたユーザーのアカウントがローカル コンピューターにない場合に発生します。  
  
### <a name="to-fix-this-problem"></a>この問題を解決するには  
  
-   リモート コンピューターで msvsmon を実行しているユーザー アカウントと同じ名前およびパスワードを使用して、Visual Studio デバッガー ホスト コンピューターにユーザー アカウントを追加します。  
  
     \- または -  
  
-   ローカル コンピューターを呼び出すアクセス許可を持つユーザーとして msvsmon を実行します。 つまり、ユーザーは msvsmon コンピューターのドメイン ユーザーおよび管理者である必要があります。 msvsmon を実行するユーザー アカウントは次の 2 とおりの方法で指定できます。  
  
    -   Msvsmon アイコンを右クリックし **実行**ショートカット メニューの   
  
     \- または -  
  
    -   コマンド プロンプトで `runas.exe` を実行します。  
  
## <a name="see-also"></a>関連項目  
 [リモート ドメイン間でのデバッグ](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



