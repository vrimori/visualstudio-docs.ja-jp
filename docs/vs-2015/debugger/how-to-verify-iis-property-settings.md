---
title: '方法: IIS のプロパティ設定を確認します |。Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4639055fe9320c8fd1bf1b2575bca323642dd17f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742071"
---
# <a name="how-to-verify-iis-property-settings"></a>方法 : IIS のプロパティ設定を確認する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IIS 管理ツールで、Web アプリケーションのプロパティを設定できます。 これらのプロパティは、実行するアプリケーションに合わせて正しく設定する必要があります。そのため、トラブルシューティングのときに、多くの場合、設定を確認することが必要になります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Web アプリケーションの IIS 設定をチェックするには  
  
1.  開く、**管理ツール**ウィンドウ: で、**開始**メニューで、**プログラム**、順にクリックします**管理ツール**します。 場合**管理ツール**に表示されない、**プログラム**メニューから、[検索対象] で、**コントロール パネルの**です。  
  
    -   Windows 2000 では、次のように選択します。**インターネット サービス マネージャー**します。  
  
    -   Windows xp では、次のように選択します。**インターネット インフォメーション サービス**します。  
  
    -   Windows Server 2003 でダブルクリック**サーバーの役割管理**します。  
  
         **サーバーの役割管理**ウィンドウが開きます。 [**アプリケーション サーバー**、] をクリックして**このアプリケーション サーバー管理**します。  
  
         **アプリケーション サーバー**ウィンドウが開きます。 開く、**インターネット インフォメーション サービス (IIS) マネージャー**左側のウィンドウでノード。  
  
2.  ダイアログ ボックスで、使用しているコンピューターのツリー コントロール ノードをクリックします。 をクリックして、 **Websites**ノード、Web アプリケーションのノードを選択します。 Web サイトのノードと、それに伴っての兄弟になりますか、**既定の Web サイト**ノード、または既存の Web サイト ノードの下に仮想ディレクトリ ノードです。  
  
3.  Web アプリケーションを右クリックし、ショートカット メニューで、**プロパティ**します。  
  
4.  Web アプリケーションのセキュリティ設定を確認します。  
  
    1.  Web アプリケーションで**プロパティ**ウィンドウで、をクリックして、**ディレクトリ セキュリティ**タブをクリックし、をクリックして**編集**します。  
  
    2.  **認証方法**ダイアログ ボックスで、**匿名アクセスの有効化**と**統合 Windows 認証**選択されていない場合。  
  
    3.  をクリックして**OK**を閉じる、**認証方法** ダイアログ ボックス。  
  
5.  ATL Server アプリケーションの場合は、DEBUG の動詞が ISAPI 拡張機能に関連付けられていることを確認してください。 詳細については、次を参照してください。[方法: 拡張機能とデバッグ動詞を関連付ける](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e)します。  
  
6.  [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]アプリケーションでは、必ず仮想フォルダー、アプリケーション設定されたアプリケーション名**インターネット インフォメーション サービス (IIS) マネージャー**、**インターネット サービス マネージャー**または**インターネット インフォメーション サービス**します。  
  
    1.  Web アプリケーションで**プロパティ**ウィンドウで、**ディレクトリ**タブの場合は、アプリケーションが仮想ディレクトリ、または**ホーム ディレクトリ** タブで、アプリケーションの場合Web サイトです。  
  
    2.  いることを確認の名前、**ローカル パス**実際に配置されたアプリケーション ディレクトリの名前に一致します。  
  
    3.  **アプリケーション設定**アプリケーションを含むルート ディレクトリの名前を入力します。  
  
    4.  クリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
7.  [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]アプリケーションでは、をクリックして、 **ASP.NET** タブであることを確認し、正しいバージョンの[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]が指定されています。  
  
8.  クリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
9. をクリックして**OK**を閉じる、**インターネット インフォメーション サービス (IIS) マネージャー**、**インターネット サービス マネージャー**、または**インターネット インフォメーション サービス** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [トラブルシューティング](../debugger/debugging-web-applications-troubleshooting.md)



