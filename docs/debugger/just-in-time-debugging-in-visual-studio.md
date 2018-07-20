---
title: '方法: - Just-in-time デバッガーへの応答 |Microsoft Docs'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cec8887ddf2023a8abd08f409b93f47efdc7001
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155569"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>方法: - Just-in-time デバッガーへの応答

時にのみ表示される場合に行う必要がありますアクション デバッガー ダイアログ ボックスでは、何を行うに依存します。

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>解決する方法 (Visual Studio のユーザー) のエラーをデバッグする場合

- 必要があります[Visual Studio がインストールされている](http://visualstudio.microsoft.com)デバッグしようとして、エラーに関する詳細情報を表示します。 詳細については、次を参照してください。 [Just-In-Time デバッガーを使用してデバッグ](../debugger/debug-using-the-just-in-time-debugger.md)します。 エラーを解決することはできません、アプリを修正する場合は、エラーを解決するのには、アプリの所有者に問い合わせてください。

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Just-In-Time デバッガー ダイアログ ボックスが表示されないようにする場合

Just ポイントイン タイムを防ぐために手順を実行することができますデバッガー ダイアログ ボックスが表示されません。 アプリでは、エラーを処理する場合は、通常、アプリを実行できます。

1. (Web アプリ)Web アプリを実行しようとする場合は、スクリプトのデバッグを無効にできます。

    Internet Explorer または Edge では、[インターネット オプション] ダイアログ ボックスでスクリプトのデバッグを無効にします。 これらの設定にアクセスすることができます、**コントロール パネルの** > **ネットワークとインターネット** > **インターネット オプション**(正確な手順が異なります、Windows のバージョンおよびお使いのブラウザー)。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    エラーを確認したところ、web ページを閉じてください。 この設定を変更しても問題が解決しない場合は、問題を解決する web アプリの所有者にお問い合わせください。

3. (Visual Studio のユーザー)Visual Studio のインストールがある (または以前にインストールし、削除した場合)、[デバッグを使用しないジャスト イン タイム](../debugger/debug-using-the-just-in-time-debugger.md)再度アプリを実行しようとします。

    > [!IMPORTANT]
    > ジャスト イン タイムを無効にした場合のデバッグと、アプリで未処理の例外 (エラー) が発生した、標準エラー ダイアログが代わりに、表示されますか、または、アプリのクラッシュやハングします。 (ユーザーまたはアプリの所有者の) によって、エラーが修正されるまで、アプリは通常どおり実行されません。

2. (ASP.NET および IIS)IIS で ASP.NET Web アプリをホストしている場合は、サーバー側のデバッグを無効にします。

    IIS マネージャーで、サーバー ノードを右クリックし、選択**機能ビューに切り替える**します。 [ASP.NET] セクションで次のように選択します。 **.NET コンパイル**選択するかどうかを確認して、 **False** (手順では古いバージョンの IIS で異なります) のデバッグ動作として。

## <a name="see-also"></a>関連項目
 [デバッガーの基本事項](../debugger/debugger-basics.md)
