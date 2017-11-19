---
title: "エラー: Windows ファイル共有が構成されました... |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: afda40aea2340f85d27218b5a9cd7c4f09f64201
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="error-windows-file-sharing-has-been-configured"></a>エラー : Windows ファイル共有が構成されました。
別のユーザー名を使用してリモート コンピューターに接続できるように Windows ファイル共有が構成されました。 この設定はリモート デバッグと互換性がありません。  
  
 現在のファイル共有の構成は、別のユーザー名を使用してリモート コンピューターに接続するようにセットアップされています。 このシナリオでは、リモート デバッグを実行できません。  
  
 このエラーを解決するには、他のアカウント名を使用してコンピューターにログオンするか、デバッグを実行しているアカウント名を使用するようにファイル共有を変更します。  
  
 このユーザー名を使用してリモート コンピューターに接続する場合は、まずリモート コンピューターから切断する必要があります。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  他のアカウント名を使用してローカル コンピューター (デバッグを起動したコンピューター) にログオンします。  
  
     または  
  
     」を参照してください。 リモート コンピューターから切断します。次に、自分のアカウント名を使用して他のコンピューターに接続するようにファイル共有を再構成します。  
  
    1.  **開始** メニューのをポイント**アクセサリ**、クリックして**コマンド プロンプト**です。  
  
    2.  Windows のコマンド プロンプトで、次のように入力します。  
  
         `net use /delete computer_name`  
  
    3.  Windows ヘルプに記載されているいずれかの方法を使用して、ファイル共有の設定を変更します。