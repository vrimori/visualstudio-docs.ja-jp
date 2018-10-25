---
title: 'エラー: 必要はありません、プロセスを検査するアクセス許可&#39;id |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7577ac0c2d6b876c3055a90a915e48ea2177bc5b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196912"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>エラー: 必要はありません、プロセスを検査するアクセス許可&#39;id
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロセスの ID を検査する権限がありません。 これは、システムの混が原因である可鉢があります。  
  
 デバッグに必要なプロセス ID をデバッガーが検査できませんでした。 最も可能性の高い原因として、ターミナル サービスが無効になっていることが挙げられます。 既定では、ターミナル サービスが有効に設定されています。 再度有効にするには、次の手順に従います。  
  
### <a name="to-enable-terminal-services"></a>ターミナル サービスを有効にするには  
  
1.  をクリックして**開始**を選択し**コントロール パネルの**です。  
  
2.  コントロール パネルで、次のように選択します。**クラシック表示に切り替える**、必要に応じて、し、ダブルクリック**管理ツール**します。  
  
3.  **管理ツール**ウィンドウで、ダブルクリックして**コンピュータの管理**します。  
  
4.  コンピューターの管理 ウィンドウで、**サービスとアプリケーション**ノード。  
  
5.  で、**サービスとアプリケーション**、 をクリックして**サービス**します。  
  
     右側のパネルにサービスの一覧が表示されます。  
  
6.  **サービス**一覧で、右クリックして**ターミナル サービス**選び、**プロパティ**します。  
  
7.  **ターミナル サービスのプロパティ**ウィンドウに移動して、**全般** タブで設定し、**スタートアップの種類**に**手動**。  
  
8.  **[OK]** をクリックします。  
  
9. コンピューターを再起動します。  
  
     この手順では、リモート デスクトップを自動的に有効にすることはできません。 コンピューターのリモート デスクトップを有効にするには、別途、次の手順を実行する必要があります。  
  
### <a name="to-enable-remote-desktop"></a>リモート デスクトップを有効にするには  
  
1.  をクリックして**開始**し、右クリックし、**マイ コンピューター**します。  
  
2.  **[プロパティ]** を選択します。  
  
     **システム プロパティ**ウィンドウが表示されます。  
  
3.  クリックして**リモート**します。  
  
4.  **リモート デスクトップ**、**ユーザーがこのコンピューターにリモート接続を許可する**。  
  
5.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)



