---
title: '方法: IIS のプロパティ設定を確認してください |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acd232b76ece37737833d071c8551d1319d4f151
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-verify-iis-property-settings"></a>方法 : IIS のプロパティ設定を確認する
IIS 管理ツールで、Web アプリケーションのプロパティを設定できます。 これらのプロパティは、実行するアプリケーションに合わせて正しく設定する必要があります。そのため、トラブルシューティングのときに、多くの場合、設定を確認することが必要になります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Web アプリケーションの IIS 設定をチェックするには  
  
1.  開く、**管理ツール**ウィンドウ: に、**開始** メニューのをポイント**プログラム**、順にクリック**管理ツール**です。 場合**管理ツール**に表示されない、**プログラム**メニューから、[検索対象] で、**コントロール パネルの**です。  
  
    -   Windows 2000 では、選択**インターネット サービス マネージャー**です。  
  
    -   Windows XP では**インターネット インフォメーション サービス**です。  
  
    -   Windows Server 2003 でダブルクリック**サーバーの役割管理**です。  
  
         **サーバーの役割管理**ウィンドウが開きます。 **アプリケーション サーバー**をクリックして**このアプリケーション サーバーを管理**です。  
  
         **アプリケーション サーバー**ウィンドウが開きます。 開く、**インターネット インフォメーション サービス (IIS) マネージャー**左側のウィンドウ内のノードです。  
  
2.  ダイアログ ボックスで、使用しているコンピューターのツリー コントロール ノードをクリックします。 をクリックして、 **Web サイト**ノード、Web アプリケーションのノードを選択します。 ある Web サイトのノードであるための兄弟、 **Default Web Site**ノード、または既存の Web サイト ノード下にある仮想ディレクトリ ノードです。  
  
3.  Web アプリケーションを右クリックし、ショートカット メニューをクリックして**プロパティ**です。  
  
4.  Web アプリケーションのセキュリティ設定を確認します。  
  
    1.  Web アプリケーションで**プロパティ**ウィンドウで、をクリックして、**ディレクトリ セキュリティ**タブをクリックし、をクリックして**編集**です。  
  
    2.  **認証方法**ダイアログ ボックスで、**匿名アクセスの有効化**と**統合 Windows 認証**既に選択されていない場合。  
  
    3.  をクリックして**OK**を閉じる、**認証方法** ダイアログ ボックス。  
  
5.  ATL Server アプリケーションの場合は、DEBUG の動詞が ISAPI 拡張機能に関連付けられていることを確認してください。 詳細については、次を参照してください。[する方法: 拡張機能とデバッグ動詞を関連付ける](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e)です。  
  
6.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]アプリケーションでは、必ず仮想フォルダーに、アプリケーションで設定されたアプリケーション名には、**インターネット インフォメーション サービス (IIS) マネージャー**、**インターネット サービス マネージャー**または**インターネット インフォメーション サービス**です。  
  
    1.  Web アプリケーションで**プロパティ**ウィンドウで、**ディレクトリ** タブの 仮想ディレクトリがアプリケーションの場合、または**ホーム ディレクトリ** タブの場合は、アプリケーションがWeb サイトです。  
  
    2.  いることを確認の名前、**ローカル パス**がアプリケーションを実際に配置したディレクトリの名前に一致します。  
  
    3.  **アプリケーション設定**アプリケーションを含むルート ディレクトリの名前を入力します。  
  
    4.  をクリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
7.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]アプリケーションでは、をクリックして、 **ASP.NET** タブであることを確認し、正しいバージョンの[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]が指定されています。  
  
8.  をクリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
9. をクリックして**OK**を閉じる、**インターネット インフォメーション サービス (IIS) マネージャー**、**インターネット サービス マネージャー**、または**インターネット インフォメーション サービス** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [トラブルシューティング](../debugger/debugging-web-applications-troubleshooting.md)