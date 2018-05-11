---
title: 'エラー: 別のユーザーとして、Microsoft Visual Studio リモート デバッグ モニター、リモート コンピューターでが実行されている |Microsoft ドキュメント'
ms.custom: ''
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
ms.openlocfilehash: e2bdc731b65a8d451b6882914e8bed1abca2139b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>エラー : リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。
リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
 リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。  
  
## <a name="cause"></a>原因  
 このメッセージは、認証なしモードでのデバッグ中に、msvsmon を起動したユーザーが Visual Studio を実行中のユーザーと一致しない場合に発生します。  
  
## <a name="solution"></a>ソリューション  
 最も安全で適切な解決策は、Visual Studio と同じユーザー アカウントでリモート デバッグ モニター (msvsmon.exe) を実行することです。 他のアカウントでリモート デバッグ モニターを実行することができますができない場合、**任意のユーザーにデバッグを許可する**、リモート デバッグ モニターで選択したオプション**オプション** ダイアログ ボックス。  
  
> [!CAUTION]
>  他のユーザーに接続する許可を与えると、誤ったリモート デバッグ セッションに接続してしまう可能性があります。 デバッグ**認証なし**モードがセキュリティで保護することはありませんし、注意して使用する必要があります。
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)