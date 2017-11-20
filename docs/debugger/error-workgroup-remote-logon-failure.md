---
title: "エラー: ワークグループ リモート ログオン エラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0c52907e8735136b317200bf915ddbc76f9c5cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="error-workgroup-remote-logon-failure"></a>エラー : ワークグループ リモート ログオン エラー
このエラーには、次のメッセージが表示されます。  
  
 ログオン エラー: 不明なユーザー名、または不適切なパスワードです。  
  
 **原因**  
  
 このエラーは、ワークグループのコンピューターからデバッグしているときにリモート コンピューターに接続しようとすると発生することがあります。 以下の原因が考えられます。  
  
-   名前とパスワードが一致するアカウントがリモート コンピューター上に存在しない。  
  
-   既定値によってこのエラーが発生する場合は、Visual Studio コンピューターとリモート コンピューターの両方がワークグループに、**ローカル セキュリティ ポリシー**リモート マシンで設定します。 既定の設定、**ローカル セキュリティ ポリシー**設定は**Guest のみ - ローカル ユーザーが Guest として認証**です。 このセットアップでデバッグするをリモート コンピューターで設定を変更する必要があります**クラシック - ローカル ユーザー自身として認証**です。  
  
> [!NOTE]
>  次のタスクを実行するには、管理者権限が必要です。  
  
### <a name="to-open-the-local-security-policy-window"></a>[ローカル セキュリティ ポリシー] ウィンドウを開くには  
  
1.  開始、 **secpol.msc** Microsoft 管理コンソール スナップインです。 Windows Search、[ファイル名を指定して実行] ボックス、またはコマンド プロンプトで「secpol.msc」と入力します。  
  
### <a name="to-add-user-rights-assignments"></a>ユーザー権限の割り当てを追加するには  
  
1.  開く、**ローカル セキュリティ ポリシー**ウィンドウです。  
  
2.  展開して、**ローカル ポリシー**フォルダーです。  
  
3.  をクリックして**ユーザー権利の割り当て**です。  
  
4.  **ポリシー**列をダブルクリックして**プログラムのデバッグ**を現在のローカル グループ ポリシーの割り当てを表示する、**ローカル セキュリティ ポリシーの設定** ダイアログ ボックス。  
  
     ![ローカル セキュリティ ポリシーのユーザー権限](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  新しいユーザーを追加する] をクリックして、 **[ユーザーまたはグループ**ボタンをクリックします。  
  
### <a name="to-change-the-sharing-and-security-model"></a>共有とセキュリティ モデルを変更するには  
  
1.  開く、**ローカル セキュリティ ポリシー**ウィンドウです。  
  
2.  展開して、**ローカル ポリシー**フォルダーです。  
  
3.  をクリックして**セキュリティ オプション**です。  
  
4.  **ポリシー**列をダブルクリックして**ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル**です。  
  
5.  **ネットワーク アクセス: ローカル アカウントの共有とセキュリティ モデル** ダイアログ ボックスで、値を変更**クラシック - ローカル ユーザー自身として認証** をクリックし、**適用**ボタンをクリックします。  
  
     ![ローカル セキュリティ ポリシーのセキュリティ オプション](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)