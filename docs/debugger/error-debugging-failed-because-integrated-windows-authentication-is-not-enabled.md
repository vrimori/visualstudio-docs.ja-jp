---
title: 'エラー: デバッグ、統合 Windows 認証が有効になっていないために失敗しました |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f56cca9fa637efaa66b6dcab4716d4a1900aa61d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278646"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>エラー ： Windows 統合認証が無効になっているため、デバッグに失敗しました。
デバッグを要求したユーザーの認証が認証エラーで失敗しました。 このエラーは、Web アプリケーションまたは XML Web サービスにステップ インしようとするときに発生することがあります。 このエラーの原因の 1 つとして、統合 Windows 認証が有効ではないことが挙げられます。 その機能を有効にする場合は、「統合 Windows 認証を有効にするには」の手順を実行します。  
  
 統合 Windows 認証を有効にした、このエラーが表示される場合は、ために、このエラーが発生したことが**Windows ドメイン サーバーでダイジェスト認証を**を有効にします。 この場合は、ネットワーク管理者に問い合わせてください。  
  
### <a name="to-enable-integrated-windows-authentication"></a>統合 Windows 認証を有効にするには  
  
1.  管理者アカウントを使って Web サーバーにログオンします。  
  
2.  クリックして**開始**順にクリックします**コントロール パネルの **します。  
  
3.  **コントロール パネルの **、ダブルクリックして**管理ツール**します。  
  
4.  ダブルクリック**インターネット インフォメーション サービス**します。  
  
5.  Web サーバー ノードをクリックします。  
  
     A **Websites**サーバー名の下にフォルダーが表示されます。  
  
6.  認証の設定は、すべての Web サイトまたは個々の Web サイトについて行うことができます。 すべての Web サイトの認証を構成するを右クリックし、 **Websites**フォルダーをクリック**プロパティ**します。 個々 の Web サイトの認証を構成するには、開く、 **Websites**フォルダー、個々 の Web サイトを右クリックし、順にクリックします**プロパティ**します。  
  
     **プロパティ** ダイアログ ボックスが表示されます。  
  
7.  をクリックして、**ディレクトリ セキュリティ**タブ。  
  
8.  **匿名アクセスおよび認証コントロール**セクションで、**編集**します。  
  
     **認証方法** ダイアログ ボックスが表示されます。  
  
9. **認証済みアクセス**、**統合 Windows 認証**。  
  
10. をクリックして**OK**を閉じる、**認証方法** ダイアログ ボックス。  
  
11. クリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
12. 閉じる、**インターネット インフォメーション サービス**ウィンドウ。  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/IIS 7 で統合 Windows 認証を有効にするには  
  
1.  管理者アカウントを使って Web サーバーにログオンします。  
  
2.  Windows 認証と II6 管理互換の機能を有効にするために、以下の手順をまだ実行していなければ、この手順を実行します。  
  
    1.  をクリックして**開始**、 をクリックして**コントロール パネルの**をクリックし、**プログラム**です。  
  
    2.  [**プログラムと機能**、] をクリックして**オンまたはオフにする Windows 機能**します。  
  
         続行するかどうかの確認を求める [ユーザー アカウント制御] ダイアログ ボックスが表示されます。  
  
    3.  **[続行]** をクリックします。  
  
         [Windows の機能] ダイアログ ボックスが表示されます。  
  
    4.  機能の一覧で、展開、**インターネット インフォメーション サービス**ノード。  
  
    5.  **インターネット インフォメーション サービス**、展開、 **World Wide Web サービス**ノード。  
  
    6.  [ **World Wide Web サービス**、] をクリックして**セキュリティ**します。  
  
    7.  クリックして**Windows 認証**します。  
  
    8.  **インターネット インフォメーション サービス**、展開、 **Web 管理ツール**ノード。  
  
    9. **Web 管理ツール**、展開、 **IIS 6 管理互換**ノード、および選択、 **IIS 6 メタベースおよび IIS 6 構成との互換性**チェック ボックスをオンします。  
  
    10. **Web 管理ツール**を選択します**IIS 管理コンソール** をクリック**ok をクリックします。**  
  
    11. コンピューターを再起動して、これらの変更を反映します。  
  
3.  をクリックして**開始**] をクリックし、**コントロール パネルの [** します。  
  
4.  クリックして**クラシック表示**、し、ダブルクリック**管理ツール**します。  
  
5.  **名前**列をダブルクリックします**インターネット インフォメーション サービス (IIS) マネージャー**します。  
  
6.  **接続**列で、サーバーのノードを展開します。  
  
     A **Websites**サーバー名の下にフォルダーが表示されます。  
  
7.  展開、 **Websites**ノード統合 Windows 認証を有効にする Web サイトをクリックします。  
  
8.  中央のペインのタイトルが、選択した Web サイトの名前に変わります。 このウィンドウで 、 **IIS**見出しをダブルクリックして**認証**します。  
  
     ウィンドウのタイトルを変更する**認証**します。  
  
9. **認証**ウィンドウで、**名前**列を右クリックして**Windows 認証**順にクリックします**を有効にする**します。  
  
10. 閉じる、**インターネット インフォメーション サービス (IIS) マネージャー**ウィンドウ。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ: エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft ダイジェスト認証](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [IIS 7.0 で Windows Vista での Web アプリケーションと Visual Studio を実行します。](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)