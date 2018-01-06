---
title: "エラー: 必要はありません、プロセス &#39; を検査する権限 id |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f51087d4f7882c34826942a898328640107a5ac6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>エラー: 必要はありません、プロセス &#39; を検査する権限 id
プロセスの ID を検査する権限がありません。 これは、システムの混が原因である可鉢があります。  
  
 デバッグに必要なプロセス ID をデバッガーが検査できませんでした。 最も可能性の高い原因として、ターミナル サービスが無効になっていることが挙げられます。 既定では、ターミナル サービスが有効に設定されています。 再度有効にするには、次の手順に従います。  
  
### <a name="to-enable-terminal-services"></a>ターミナル サービスを有効にするには  
  
1.  をクリックして**開始**を選択し**コントロール パネルの** です。  
  
2.  コントロール パネルで、次のように選択します。**クラシック表示に切り替える**、必要に応じて、順にダブルクリック**管理ツール**です。  
  
3.  **管理ツール**ウィンドウをダブルクリックして**コンピューターの管理**です。  
  
4.  コンピューターの管理 ウィンドウで、展開、**サービスとアプリケーション**ノード。  
  
5.  下にある、**サービスとアプリケーション**をクリックして**Services**です。  
  
     右側のパネルにサービスの一覧が表示されます。  
  
6.  **Services**ボックスの一覧を右クリックして**ターミナル サービス**を選択し**プロパティ**です。  
  
7.  **ターミナル サービスのプロパティ**ウィンドウに移動して、**全般** タブで設定し、**スタートアップの種類**に**手動**です。  
  
8.  **[OK]**をクリックします。  
  
9. コンピューターを再起動します。  
  
     この手順では、リモート デスクトップを自動的に有効にすることはできません。 コンピューターのリモート デスクトップを有効にするには、別途、次の手順を実行する必要があります。  
  
### <a name="to-enable-remote-desktop"></a>リモート デスクトップを有効にするには  
  
1.  をクリックして**開始**し、右クリックし、**マイ コンピューター**です。  
  
2.  選択**プロパティ**です。  
  
     **システム プロパティ**ウィンドウが表示されます。  
  
3.  をクリックして**リモート**です。  
  
4.  **リモート デスクトップ****ユーザーをこのコンピューターにリモートで接続できるように**です。  
  
5.  **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)