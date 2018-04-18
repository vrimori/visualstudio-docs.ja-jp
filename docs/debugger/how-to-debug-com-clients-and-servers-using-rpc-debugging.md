---
title: '方法: COM クライアントとサーバーが RPC デバッグを使用してデバッグ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4fe212015b381a38ed1cf110189b6e4839fdf9f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>方法 : RPC デバッグを使用して COM クライアントおよびサーバーをデバッグする
リモート プロシージャ コール (RPC: Remote Procedure Call) デバッグを使用して、COM クライアント/サーバー アプリケーションをデバッグできます。 このデバッグを行うには、あらかじめ RPC デバッグを有効にする必要があります。 RPC デバッグを有効にすると、ステップ実行でクライアントからサーバーを呼び出すときに、デバッガーがサーバーにアタッチし、コードのデバッグができるようになります。 デバッガーをアタッチすることにより、クライアントおよびサーバーのどちらのプロセスでも、デバッガーのすべての機能を使用できます。  
  
### <a name="to-enable-rpc-debugging"></a>RPC デバッグを有効にするには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **オプション** ダイアログ ボックスをクリックして、**デバッグ**フォルダーです。  
  
3.  クリックして、**ネイティブ**ページ。  
  
4.  選択、 **RPC デバッグ**チェック ボックスをオンします。  
  
    > [!NOTE]
    >  RPC 呼び出しをデバッグするには、管理者またはパワー ユーザーの権限が必要です。  
  
    > [!NOTE]
    >  Microsoft Windows Vista が実行されているリモート サーバーへの RPC ステップ実行は、そのリモート サーバーにネイティブ デバッガーがアタッチされている場合のみ機能します。 それ以外の場合、エラー メッセージが表示されることなく RPC 呼び出しが失敗します。 何らかの方法で RPC 呼び出しに成功したとしても、RPC 呼び出しへのステップ インは正常に機能しません。  
  
## <a name="see-also"></a>関連項目  
 [COM サーバーおよび COM コンテナーのデバッグ](../debugger/com-server-and-container-debugging.md)  
 [Visual Studio でデバッグ](../debugger/index.md)[デバッガーの機能のツアー](../debugger/debugger-feature-tour.md)