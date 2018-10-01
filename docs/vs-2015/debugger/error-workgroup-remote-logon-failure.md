---
title: 'エラー: ワークグループ リモート ログオン エラー |Microsoft Docs'
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
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46d7043eba9d357f410d1a05655870ef5e1121d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538154"
---
# <a name="error-workgroup-remote-logon-failure"></a>エラー : ワークグループ リモート ログオン エラー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: ワークグループ リモート ログオン エラー](https://docs.microsoft.com/visualstudio/debugger/error-workgroup-remote-logon-failure)します。  
  
このエラーには、次のメッセージが表示されます。  
  
 ログオン エラー: 不明なユーザー名、または不適切なパスワードです。  
  
 **原因**  
  
 このエラーは、ワークグループのコンピューターからデバッグしているときにリモート コンピューターに接続しようとすると発生することがあります。 以下の原因が考えられます。  
  
-   名前とパスワードが一致するアカウントがリモート コンピューター上に存在しない。  
  
-   既定値によってこのエラーが発生する場合は、Visual Studio コンピューターとリモート コンピューターの両方がワークグループに、**ローカル セキュリティ ポリシー**リモート コンピューターで設定します。 既定の設定、**ローカル セキュリティ ポリシー**設定は**Guest のみ - ローカル ユーザーをゲストとして認証**します。 このセットアップでデバッグするをリモート コンピューターで設定を変更する必要があります**クラシック - ローカル ユーザー自身として認証**します。  
  
> [!NOTE]
>  次のタスクを実行するには、管理者権限が必要です。  
  
### <a name="to-open-the-local-security-policy-window"></a>[ローカル セキュリティ ポリシー] ウィンドウを開くには  
  
1.  開始、 **secpol.msc** Microsoft 管理コンソール スナップインです。 Windows Search、[ファイル名を指定して実行] ボックス、またはコマンド プロンプトで「secpol.msc」と入力します。  
  
### <a name="to-add-user-rights-assignments"></a>ユーザー権限の割り当てを追加するには  
  
1.  ローカル セキュリティ ポリシーを開きます。  
  
2.  開く、**ローカル セキュリティ ポリシー**ウィンドウ。  
  
3.  展開、**ローカル ポリシー**フォルダー。  
  
4.  クリックして**ユーザー権利の割り当て**します。  
  
5.  **ポリシー**列、ダブルクリック**プログラムをデバッグ**で現在のローカル グループ ポリシーの割り当てを表示する、**ローカル セキュリティ ポリシーの設定** ダイアログ ボックス。  
  
     ![ローカル セキュリティ ポリシーのユーザー権限](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  新しいユーザーを追加する をクリックして、**追加のユーザーまたはグループ**ボタンをクリックします。  
  
### <a name="to-change-the-sharing-and-security-model"></a>共有とセキュリティ モデルを変更するには  
  
1.  開く、**ローカル セキュリティ ポリシー**ウィンドウ。  
  
2.  展開、**ローカル ポリシー**フォルダー。  
  
3.  クリックして**セキュリティ オプション**します。  
  
4.  **ポリシー**列で、ダブルクリックして**ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル**します。  
  
5.  **ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル** ダイアログ ボックスで、値を変更**クラシック - ローカル ユーザー自身として認証** をクリックし、**適用**ボタンをクリックします。  
  
     ![ローカル セキュリティ ポリシーのセキュリティ オプション](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



