---
title: '方法: COM クライアントおよびサーバーの RPC デバッグを使用したデバッグ |Microsoft Docs'
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
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b64c01f502dbe4194561776f121e21475d61d43
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536415"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>方法 : RPC デバッグを使用して COM クライアントおよびサーバーをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: デバッグの COM クライアントとサーバーを使用して RPC デバッグ](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging)します。  
  
リモート プロシージャ コール (RPC: Remote Procedure Call) デバッグを使用して、COM クライアント/サーバー アプリケーションをデバッグできます。 このデバッグを行うには、あらかじめ RPC デバッグを有効にする必要があります。 RPC デバッグを有効にすると、ステップ実行でクライアントからサーバーを呼び出すときに、デバッガーがサーバーにアタッチし、コードのデバッグができるようになります。 デバッガーをアタッチすることにより、クライアントおよびサーバーのどちらのプロセスでも、デバッガーのすべての機能を使用できます。  
  
### <a name="to-enable-rpc-debugging"></a>RPC デバッグを有効にするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション**ダイアログ ボックスで、をクリックして、**デバッグ**フォルダー。  
  
3.  をクリックして、**ネイティブ**ページ。  
  
4.  選択、 **RPC デバッグ**チェック ボックスをオンします。  
  
    > [!NOTE]
    >  RPC 呼び出しをデバッグするには、管理者またはパワー ユーザーの権限が必要です。  
  
    > [!NOTE]
    >  Microsoft Windows Vista が実行されているリモート サーバーへの RPC ステップ実行は、そのリモート サーバーにネイティブ デバッガーがアタッチされている場合のみ機能します。 それ以外の場合、エラー メッセージが表示されることなく RPC 呼び出しが失敗します。 何らかの方法で RPC 呼び出しに成功したとしても、RPC 呼び出しへのステップ インは正常に機能しません。  
  
## <a name="see-also"></a>関連項目  
 [COM サーバーおよびコンテナーのデバッグ](../debugger/com-server-and-container-debugging.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)



