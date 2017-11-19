---
title: "エラー: デバッグ統合 Windows 認証が有効でないために失敗しました |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords: debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88747922ae486adf65d2babe7a349e9538e8c9c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>エラー ： Windows 統合認証が無効になっているため、デバッグに失敗しました。
デバッグを要求したユーザーの認証が認証エラーで失敗しました。 このエラーは、Web アプリケーションまたは XML Web サービスにステップ インしようとするときに発生することがあります。 このエラーの原因の 1 つとして、統合 Windows 認証が有効ではないことが挙げられます。 その機能を有効にする場合は、「統合 Windows 認証を有効にするには」の手順を実行します。  
  
 統合 Windows 認証を有効にした、このエラーが表示される場合は、可能であればために、このエラーが発生した**Windows ドメイン サーバーでダイジェスト認証を**を有効にします。 この場合は、ネットワーク管理者に問い合わせてください。  
  
### <a name="to-enable-integrated-windows-authentication"></a>統合 Windows 認証を有効にするには  
  
1.  管理者アカウントを使って Web サーバーにログオンします。  
  
2.  をクリックして**開始**] をクリックし、**コントロール パネルの [**です。  
  
3.  **コントロール パネルの **をダブルクリックして**管理ツール**です。  
  
4.  ダブルクリックして**インターネット インフォメーション サービス**です。  
  
5.  Web サーバー ノードをクリックします。  
  
     A **Websites**サーバー名の下にフォルダーが表示されます。  
  
6.  認証の設定は、すべての Web サイトまたは個々の Web サイトについて行うことができます。 すべての Web サイトの認証を構成するを右クリックして、 **Websites**フォルダーをクリックして**プロパティ**です。 個々 の Web サイトの認証を構成するのには、開く、 **Websites**フォルダーは、個々 の Web サイトを右クリックし、をクリックして**プロパティ**です。  
  
     **プロパティ** ダイアログ ボックスが表示されます。  
  
7.  クリックして、**ディレクトリ セキュリティ**タブです。  
  
8.  **匿名アクセスおよび認証コントロール**セクションで、**編集**です。  
  
     **認証方法** ダイアログ ボックスが表示されます。  
  
9. **認証済みアクセス****統合 Windows 認証**です。  
  
10. をクリックして**OK**を閉じる、**認証方法** ダイアログ ボックス。  
  
11. をクリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
12. 閉じる、**インターネット インフォメーション サービス**ウィンドウです。  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/IIS 7 で統合 Windows 認証を有効にするには  
  
1.  管理者アカウントを使って Web サーバーにログオンします。  
  
2.  Windows 認証と II6 管理互換の機能を有効にするために、以下の手順をまだ実行していなければ、この手順を実行します。  
  
    1.  をクリックして**開始**、 をクリックして**コントロール パネルの **  をクリックし、**プログラム**です。  
  
    2.  **プログラムと機能**をクリックして**Windows の機能のオンまたはオフ**です。  
  
         続行するかどうかの確認を求める [ユーザー アカウント制御] ダイアログ ボックスが表示されます。  
  
    3.  **[続行]**をクリックします。  
  
         [Windows の機能] ダイアログ ボックスが表示されます。  
  
    4.  機能の一覧で、展開、**インターネット インフォメーション サービス**ノード。  
  
    5.  **インターネット インフォメーション サービス**、展開、 **World Wide Web サービス**ノード。  
  
    6.  **World Wide Web サービス**をクリックして**セキュリティ**です。  
  
    7.  をクリックして**Windows 認証**です。  
  
    8.  **インターネット インフォメーション サービス**、展開、 **Web 管理ツール**ノード。  
  
    9. **Web 管理ツール**、展開、 **IIS 6 管理互換**ノード、および選択、 **IIS 6 メタベースおよび IIS 6 構成との互換性**チェック ボックスをオンします。  
  
    10. **Web 管理ツール**** IIS 管理コンソール** をクリック**ok です。**  
  
    11. コンピューターを再起動して、これらの変更を反映します。  
  
3.  をクリックして**開始**] をクリックし、**コントロール パネルの [**です。  
  
4.  をクリックして**クラシック表示**、順にダブルクリック**管理ツール**です。  
  
5.  **名前**列およびダブルクリック**インターネット インフォメーション サービス (IIS) マネージャー**です。  
  
6.  **接続**列で、サーバーのノードを展開します。  
  
     A **Websites**サーバー名の下にフォルダーが表示されます。  
  
7.  展開、 **Websites**ノード統合 Windows 認証を有効にする Web サイト をクリックします。  
  
8.  中央のペインのタイトルが、選択した Web サイトの名前に変わります。 このペインで下にある、 **IIS**見出しをダブルクリックして**認証**です。  
  
     ウィンドウのタイトルを変更する**認証**です。  
  
9. **認証** ウィンドウで、**名前**列を右クリックして**Windows 認証** をクリックし、**を有効にする**です。  
  
10. 閉じる、**インターネット インフォメーション サービス (IIS) マネージャー**ウィンドウです。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ: エラーとトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft のダイジェスト認証](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [IIS 7.0 で Windows Vista で Web アプリケーションと Visual Studio を実行します。](http://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)