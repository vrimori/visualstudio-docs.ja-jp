---
title: エラー :リモート コンピューターがリモート接続 ダイアログに表示されません |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aef9a7066362f6eff58c5884993a1f85715be26
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958106"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>エラー :リモート コンピューターが [リモート接続] ダイアログに表示されません
リモート コンピューターが [リモート接続] ダイアログ ボックスに表示されない場合、下記の一般的な原因を確認してください。  
  
 マネージ互換モードを使用している場合は、Visual Studio 2010 のドキュメントをご覧ください。[トラブルシューティング (リモート デバッグ) - Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100))します。  
  
### <a name="common-causes-for-this-error"></a>このエラーの一般的な原因  
  
-   リモート コンピューターが別のサブネット内に存在するコンピューター上で実行されています。 この問題を解決するには、[修飾子] ダイアログ ボックスで、コンピューター名または IP アドレスを手動で入力します。  
  
-   リモート デバッガーがリモート コンピューター上で実行されていません。 この問題を解決するには、リモート デバッガーを起動します。  
  
-   ファイアウォールで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにファイアウォールを構成します。  
  
-   ウイルス対策ソフトウェアで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにウイルス対策ソフトウェアを構成します。  
  
## <a name="see-also"></a>「  
 [Remote Debugging](../debugger/remote-debugging.md)