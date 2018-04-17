---
title: '方法: - Just-in-time デバッガーに応答 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 05/23/17
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4da0cad183aa39e26c39f48bca401194c9eab2f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>方法: - Just-in-time デバッガーへの応答

表示されたら、ジャスト イン タイムが行うアクションを行うには対象の依存するデバッガー ダイアログ ボックス。

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>修正するか、エラー (Visual Studio ユーザー) をデバッグする場合

- 必要があります[Visual Studio がインストールされて](https://www.microsoft.com/en-us/download/details.aspx?id=48146)エラーに関する詳細情報を表示し、それをデバッグしようとしています。 詳細については、次を参照してください。 [Just-In-Time デバッガーを使用してデバッグ](../debugger/debug-using-the-just-in-time-debugger.md)です。 場合はエラーを解決し、アプリを修正することはできません、エラーを解決するのには、アプリの所有者に問い合わせてください。

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Just-In-Time デバッガー ダイアログ ボックスが表示されないようにする場合

ジャスト イン タイムを防止する手順を行うデバッガー ダイアログ ボックスが表示されません。 アプリでは、エラーを処理する場合は、通常、アプリを実行できます。

1. (Web アプリ)Web アプリを実行しようとする場合は、スクリプトのデバッグを無効にできます。

    Internet Explorer またはエッジでは、[インターネット オプション] ダイアログ ボックスでスクリプトのデバッグを無効にします。 これらの設定にアクセスすることができます、**コントロール パネルの** > **ネットワークとインターネット** > **インターネット オプション**(正確な手順が異なります、Windows のバージョンおよびお使いのブラウザー)。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    エラーを検出する web ページを閉じてください。 この設定を変更しても問題が解決しない場合は、問題を解決する web アプリの所有者に問い合わせてください。

3. (Visual Studio ユーザー)Visual Studio がインストール済み (またはが既にインストールされており、それを削除していた場合)、 [ジャスト イン タイムのデバッグを](../debugger/debug-using-the-just-in-time-debugger.md)再度アプリを実行しようとします。

    > [!IMPORTANT]
    > ジャスト イン タイムを無効にした場合のデバッグと、アプリで未処理の例外 (エラー) が発生した、代わりに、標準のエラー ダイアログ ボックスか表示されます、または、アプリのクラッシュやハングアップします。 (またはによって、アプリの所有者) エラーを解決するまで、アプリは通常実行されません。

2. (ASP.NET と IIS)IIS で ASP.NET Web アプリをホストしている場合は、サーバー側のデバッグを無効にします。

    IIS マネージャーでは、サーバー ノードを右クリックして、選択**機能ビューに切り替える**です。 [ASP.NET] セクションで選択**.NET コンパイル**を選択するかどうかを確認し、 **False** (手順は、IIS の旧バージョンでは異なります) のデバッグ動作として。
  
## <a name="see-also"></a>関連項目    
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
