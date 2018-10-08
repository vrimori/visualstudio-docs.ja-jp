---
title: プロセスにアタッチできません |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41eed3132039f2622c5d46b9937893ddaafa2dbf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535857"
---
# <a name="unable-to-attach-to-the-process"></a>[プロセスにアタッチできません] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[、プロセスにアタッチできませんでした。](https://docs.microsoft.com/visualstudio/debugger/unable-to-attach-to-the-process)します。  
  
プロセスにアタッチできません。 このマシンに接続中にサーバー上のデバッガー コンポーネントのアクセスが拒否されました。  
  
 このエラーは一般的に次の 2 とおりの原因で発生します。  
  
 **シナリオ 1:** コンピューター A には、Windows XP が実行されています。 コンピューター B は、Windows Server 2003 を実行しています。 コンピューター B のレジストリには、以下 DWORD 値が含まれます。  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 ユーザー 1 はコンピューター B でターミナル サーバー セッション (セッション 1) を開始し、セッションでマネージド アプリケーションを起動します。  
  
 両方のマシンでの管理者であるユーザー、2 は、コンピューター A にログオンしています。そこから、彼とマシン B 上のセッション 1 で実行するアプリケーションにアタッチするには  
  
 **シナリオ 2:** 両方のマシンで同じパスワードを使用して 2 つのマシン、A と B に、同じワークグループ内に 1 人のユーザーがログオンしています。 コンピューター A で、デバッガーが実行されていると、コンピューター B の A で実行されているマネージ アプリケーションにアタッチしよう**ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル**設定**ゲスト**します。  
  
### <a name="to-solve-scenario-1"></a>シナリオ 1 を解決するには  
  
-   同じユーザー アカウント名とパスワードを使って、デバッガーとマネージド アプリケーションを実行します。  
  
### <a name="to-solve-scenario-2"></a>シナリオ 2 を解決するには  
  
1.  **[スタート]** メニューの **[コントロール パネル]** をクリックします。  
  
2.  コントロール パネルで、ダブルクリック**管理ツール**します。  
  
3.  管理ツール ウィンドウでダブルクリック**ローカル セキュリティ ポリシー**します。  
  
4.  ローカル セキュリティ ポリシー ウィンドウで、次のように選択します。**ローカル ポリシー**します。  
  
5.  **ポリシー**列で、ダブルクリックして**ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル**します。  
  
6.  **ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル** ダイアログ ボックスで、ローカル セキュリティ設定を変更**クラシック**、 をクリック**OK**します。  
  
    > [!CAUTION]
    >    セキュリティ モデルを [クラシック] に変更すると、共有ファイルおよび DCOM コンポーネントへの予期しないアクセスにつながることがあります。 この変更を行うと、リモート ユーザーが、Guest ではなく、ローカル ユーザー アカウントを使用して認証を行う可能性があります。 リモート ユーザーが入力したユーザー名とパスワードが、ローカル ユーザーのものと一致したとします。その場合、リモート ユーザーは、ローカル ユーザーが共有していたすべてのフォルダーや DCOM オブジェクトにアクセスできます。このセキュリティ モデルを使用する場合は、コンピューターのすべてのユーザー アカウントに厳密なパスワードを使用するか、独立したネットワーク アイランドをデバッグする側のコンピューターとデバッグ対象のコンピューターにセットアップし、承認されていないアクセスを防止してください。  
  
7.  すべてのウィンドウを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)



