---
title: 'エラー: リモート コンピューターがリモート接続 ダイアログに表示されません |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: c52a2ebd99b052171220fd8a06f1ae7ff5dc258e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471334"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>エラー: リモート コンピューターが [リモート接続] ダイアログに表示されません
リモート コンピューターが [リモート接続] ダイアログ ボックスに表示されない場合、下記の一般的な原因を確認してください。  
  
 マネージ互換モードを使用している場合は、Visual Studio 2010 用のマニュアルの「 [リモート デバッグのトラブルシューティング - Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) 」を調べてください。  
  
### <a name="common-causes-for-this-error"></a>このエラーの一般的な原因  
  
-   リモート コンピューターが別のサブネット内に存在するコンピューター上で実行されています。 この問題を解決するには、[修飾子] ダイアログ ボックスで、コンピューター名または IP アドレスを手動で入力します。  
  
-   リモート デバッガーがリモート コンピューター上で実行されていません。 この問題を解決するには、リモート デバッガーを起動します。  
  
-   ファイアウォールで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにファイアウォールを構成します。  
  
-   ウイルス対策ソフトウェアで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにウイルス対策ソフトウェアを構成します。  
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)