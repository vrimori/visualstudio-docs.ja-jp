---
title: エラー :リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1cb477cf852d0e07bf14f344b3dc27b20a56de59
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067734"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>エラー :リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。
リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
 リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。  
  
## <a name="cause"></a>原因  
 このメッセージは、認証なしモードでのデバッグ中に、msvsmon を起動したユーザーが Visual Studio を実行中のユーザーと一致しない場合に発生します。  
  
## <a name="solution"></a>ソリューション  
 最も安全で適切な解決策は、Visual Studio と同じユーザー アカウントでリモート デバッグ モニター (msvsmon.exe) を実行することです。 これができない場合は、リモート デバッグ モニターの **[オプション]** ダイアログ ボックスの **[すべてのユーザーにデバッグを許可する]** をオンにして他のアカウントでリモート デバッグ モニターを実行します。  
  
> [!CAUTION]
>  他のユーザーに接続する許可を与えると、誤ったリモート デバッグ セッションに接続してしまう可能性があります。 **認証なし**モードでのデバッグは決して安全ではなく、使用には注意が必要です。
  
## <a name="see-also"></a>参照  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)