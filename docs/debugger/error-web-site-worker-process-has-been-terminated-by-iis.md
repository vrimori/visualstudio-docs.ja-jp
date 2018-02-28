---
title: "エラー: Web サイト ワーカー プロセスが終了した IIS によって |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fb7a0220cf6650aeeb12ec6549d112a39918de3f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>エラー : Web サイトのワーカー プロセスが IIS によって停止されました
デバッガーが Web サイト上のコードの実行を停止しました。 このため、インターネット インフォメーション サービス (IIS: Internet Information Services) はワーカー プロセスが応答を停止したと見なしました。 したがって、IIS がワーカー プロセスを終了しました。  
  
 デバッグを継続するには、ワーカー プロセスが継続できるように IIS を設定する必要があります。 このエラー メッセージは、IIS 7 より古いバージョンの IIS では表示されません。  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>ワーカー プロセスを継続できるように IIS 7 を構成するには  
  
1.  開く、**管理ツール**ウィンドウです。  
  
    1.  をクリックして**開始**を選択し**コントロール パネルの** です。  
  
    2.  **コントロール パネル**、選択**クラシック表示に切り替える**、必要に応じて、順にダブルクリック**管理ツール**です。  
  
2.  **管理ツール**ウィンドウをダブルクリックして**インターネット インフォメーション サービス (IIS) マネージャー**です。  
  
     IIS マネージャーが開きます。  
  
3.  **接続** ウィンドウで、展開、\<コンピューター名 > ノードが必要な場合です。  
  
4.  下にある、\<コンピューター名 > ノードをクリックして**アプリケーション プール**です。  
  
5.  **アプリケーション プール**ボックスの一覧でアプリケーションを実行するプールの名前を右クリックし、をクリックして**詳細設定**です。  
  
6.  **詳細設定** ダイアログ ボックスで、検索、**プロセス モデル**セクションし、次のアクションのいずれかを実行します。  
  
    -   設定**Ping の有効化**に**False**です。  
  
    -   設定**Ping 最大応答時間**90 秒よりも大きい値にします。  
  
     設定**Ping の有効化**に**False**ワーカー プロセスは実行されていると、デバッグ対象のプロセスを停止するまで、ワーカー プロセスの動作を維持するかどうかをチェックから IIS を停止します。 設定**Ping 最大応答時間**に大きな値により、IIS ワーカー プロセスの監視を継続します。  
  
7.  をクリックして**OK**を閉じる、**詳細設定** ダイアログ ボックス。  
  
8.  IIS マネージャーを閉じ、**管理ツール**ウィンドウです。  
  
## <a name="see-also"></a>参照  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)