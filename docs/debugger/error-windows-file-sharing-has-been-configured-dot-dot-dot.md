---
title: "エラー: Windows ファイル共有が構成されました... |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
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
ms.openlocfilehash: 7bbd8d00a6939030068bbe6dd565fb57393d18be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-windows-file-sharing-has-been-configured"></a>エラー : Windows ファイル共有が構成されました。
別のユーザー名を使用してリモート コンピューターに接続できるように Windows ファイル共有が構成されました。 この設定はリモート デバッグと互換性がありません。  
  
 現在のファイル共有の構成は、別のユーザー名を使用してリモート コンピューターに接続するようにセットアップされています。 このシナリオでは、リモート デバッグを実行できません。  
  
 このエラーを解決するには、他のアカウント名を使用してコンピューターにログオンするか、デバッグを実行しているアカウント名を使用するようにファイル共有を変更します。  
  
 このユーザー名を使用してリモート コンピューターに接続する場合は、まずリモート コンピューターから切断する必要があります。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  他のアカウント名を使用してローカル コンピューター (デバッグを起動したコンピューター) にログオンします。  
  
     または  
  
     である必要があります。 リモート コンピューターから切断します。次に、自分のアカウント名を使用して他のコンピューターに接続するようにファイル共有を再構成します。  
  
    1.  **開始** メニューのをポイント**アクセサリ**、クリックして**コマンド プロンプト**です。  
  
    2.  Windows のコマンド プロンプトで、次のように入力します。  
  
         `net use /delete computer_name`  
  
    3.  Windows ヘルプに記載されているいずれかの方法を使用して、ファイル共有の設定を変更します。