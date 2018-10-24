---
title: 'エラー: Web サイトのワーカー プロセスが IIS によって停止されましたが |Microsoft Docs'
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
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45ade231d24fe5e544110ed338abb935adbf423f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857576"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>エラー : Web サイトのワーカー プロセスが IIS によって停止されました
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

デバッガーが Web サイト上のコードの実行を停止しました。 このため、インターネット インフォメーション サービス (IIS: Internet Information Services) はワーカー プロセスが応答を停止したと見なしました。 したがって、IIS がワーカー プロセスを終了しました。  
  
 デバッグを継続するには、ワーカー プロセスが継続できるように IIS を設定する必要があります。 このエラー メッセージは、IIS 7 より古いバージョンの IIS では表示されません。  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>ワーカー プロセスを継続できるように IIS 7 を構成するには  
  
1. 開く、**管理ツール**ウィンドウ。  
  
   1.  をクリックして**開始**を選択し**コントロール パネルの**です。  
  
   2.  **コントロール パネル**、選択**クラシック ビューに切り替えます**、必要に応じて、し、ダブルクリック**管理ツール**します。  
  
2. **管理ツール**ウィンドウで、ダブルクリックして**インターネット インフォメーション サービス (IIS) マネージャー**します。  
  
    IIS マネージャーが開きます。  
  
3. **接続**ウィンドウで、展開、\<コンピューター名 > ノードが必要な場合。  
  
4. [\<コンピューター名 >] ノードをクリックして**アプリケーション プール**。  
  
5. **アプリケーション プール**ボックスの一覧でアプリケーションを実行するプールの名前を右クリックし、順にクリックします**詳細設定**します。  
  
6. **詳細設定** ダイアログ ボックスで、検索、**プロセス モデル**セクションし、次の操作のいずれかを実行します。  
  
   - 設定**Ping の有効化**に**False**します。  
  
   - 設定**Ping 最大応答時間**90 秒よりも大きい値にします。  
  
     設定**Ping の有効化**に**False**ワーカー プロセスは引き続き実行され、デバッグ対象プロセスを停止するまでは、ワーカー プロセスを維持するかどうかをチェックから IIS を停止します。 設定**Ping 最大応答時間**大きな値には、IIS ワーカー プロセスの監視を継続します。  
  
7. をクリックして**OK**を閉じる、**詳細設定** ダイアログ ボックス。  
  
8. IIS マネージャーを閉じると、**管理ツール**ウィンドウ。  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)



