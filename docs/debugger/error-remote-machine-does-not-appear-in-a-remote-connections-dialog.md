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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da933f078c1b9b8011fe6cf21f31ecce857efbc0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991191"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>エラー :リモート コンピューターが [リモート接続] ダイアログに表示されません
リモート コンピューターが [リモート接続] ダイアログ ボックスに表示されない場合、下記の一般的な原因を確認してください。  
  
 マネージ互換モードを使用している場合は、Visual Studio 2010 のドキュメントをご覧ください。[トラブルシューティング (リモート デバッグ) - Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100))します。  
  
### <a name="common-causes-for-this-error"></a>このエラーの一般的な原因  
  
-   リモート コンピューターが別のサブネット内に存在するコンピューター上で実行されています。 この問題を解決するには、[修飾子] ダイアログ ボックスで、コンピューター名または IP アドレスを手動で入力します。  
  
-   リモート デバッガーがリモート コンピューター上で実行されていません。 この問題を解決するには、リモート デバッガーを起動します。  
  
-   ファイアウォールで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにファイアウォールを構成します。  
  
-   ウイルス対策ソフトウェアで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにウイルス対策ソフトウェアを構成します。  
  
## <a name="see-also"></a>関連項目
 [Remote Debugging](../debugger/remote-debugging.md)
