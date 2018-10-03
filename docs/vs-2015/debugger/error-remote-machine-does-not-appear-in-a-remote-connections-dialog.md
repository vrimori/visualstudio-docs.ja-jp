---
title: 'エラー: リモートのコンピューターがリモート接続 ダイアログに表示されません |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 552be1e38cdb7401af36b287b23091d754c35980
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547651"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>エラー: リモート コンピューターが [リモート接続] ダイアログに表示されません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: リモート コンピューターがリモート接続 ダイアログに表示されない](https://docs.microsoft.com/visualstudio/debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog)します。  
  
リモート コンピューターが [リモート接続] ダイアログ ボックスに表示されない場合、下記の一般的な原因を確認してください。  
  
 マネージ互換モードを使用している場合は、Visual Studio 2010 のドキュメントを確認してください:[リモート デバッグのトラブルシューティング - Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx)します。  
  
### <a name="common-causes-for-this-error"></a>このエラーの一般的な原因  
  
-   リモート コンピューターが別のサブネット内に存在するコンピューター上で実行されています。 この問題を解決するには、[修飾子] ダイアログ ボックスで、コンピューター名または IP アドレスを手動で入力します。  
  
-   リモート デバッガーがリモート コンピューター上で実行されていません。 この問題を解決するには、リモート デバッガーを起動します。  
  
-   ファイアウォールで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにファイアウォールを構成します。  
  
-   ウイルス対策ソフトウェアで、Visual Studio とリモート コンピューター間の通信がブロックされています。 これを解決するには、Visual Studio とリモート デバッガー (msvsmon) の通信を許可するようにウイルス対策ソフトウェアを構成します。  
  
## <a name="see-also"></a>関連項目  
 [デバイスのリモート ツールのセットアップ](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



