---
title: "エラー : ワークグループ リモート ログオン エラー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.workgroup_remote_logon_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ログオン エラー, リモート デバッグ"
  - "リモート デバッグ, ログオン エラー"
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# エラー : ワークグループ リモート ログオン エラー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このエラーには、次のメッセージが表示されます。  
  
 ログオン エラー: 不明なユーザー名、または不適切なパスワードです。  
  
 **原因**  
  
 このエラーは、ワークグループのコンピューターからデバッグしているときにリモート コンピューターに接続しようとすると発生することがあります。  以下の原因が考えられます。  
  
-   名前とパスワードが一致するアカウントがリモート コンピューター上に存在しない。  
  
-   Visual Studio コンピューターとリモート コンピューターの両方がワークグループに存在する場合、リモート コンピューターのローカル セキュリティ ポリシーの既定値によって、このエラーが発生することがあります。  ローカル セキュリティ ポリシーの既定値は **\[Guest のみ \- ローカル ユーザーが Guest として認証する\]** です。  このセットアップでデバッグするには、リモート コンピューターの設定を **\[クラシック \- ローカル ユーザーがローカル ユーザーとして認証する\]** に変更する必要があります。  
  
> [!NOTE]
>  次のタスクを実行するには、管理者権限が必要です。  
  
### \[ローカル セキュリティ ポリシー\] ウィンドウを開くには  
  
1.  **secpol.msc** Microsoft 管理コンソール スナップインを開始します。  Windows Search、\[ファイル名を指定して実行\] ボックス、またはコマンド プロンプトで「secpol.msc」と入力します。  
  
### ユーザー権限の割り当てを追加するには  
  
1.  ローカル セキュリティ ポリシーを開きます。  
  
2.  **\[ローカル セキュリティ ポリシー\]** ウィンドウを開きます。  
  
3.  **\[ローカル ポリシー\]** フォルダーを展開します。  
  
4.  **\[ユーザー権利の割り当て\]** をクリックします。  
  
5.  **\[ポリシー\]** 列の **\[プログラムのデバッグ\]** をダブルクリックして、**\[ローカル セキュリティ ポリシーの設定\]** ダイアログ ボックスに現在のローカル グループ ポリシーの割り当てを表示します。  
  
     ![ローカル セキュリティ ポリシーのユーザー権限](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG\_ERR\_LocalSecurityPolicy\_UserRightsDebugPrograms")  
  
6.  新しいユーザーを追加するには、**\[ユーザーまたはグループの追加\]** をクリックします。  
  
### 共有とセキュリティ モデルを変更するには  
  
1.  **\[ローカル セキュリティ ポリシー\]** ウィンドウを開きます。  
  
2.  **\[ローカル ポリシー\]** フォルダーを展開します。  
  
3.  **\[セキュリティ オプション\]** をクリックします。  
  
4.  **\[ポリシー\]** 列の **\[ネットワーク アクセス : ローカル アカウントの共有とセキュリティ モデル\]** をダブルクリックします。  
  
5.  **\[ネットワーク アクセス: 共有とローカル アカウントのセキュリティ モデル\]** ダイアログ ボックスで、値を **\[クラシック \- ローカル ユーザーがローカル ユーザーとして認証する\]** に変更し、**\[適用\]** をクリックします。  
  
     ![ローカル セキュリティ ポリシーのセキュリティ オプション](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG\_ERR\_LocalSecurityPolicy\_SecurityOptions\_NetworkAccess")  
  
## 参照  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)