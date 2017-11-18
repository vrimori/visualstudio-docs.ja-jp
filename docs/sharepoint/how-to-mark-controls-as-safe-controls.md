---
title: "方法: 安全なコントロールとしてマークが制御 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9f12b8944d9174ca885e90b92c8e3a0d0b83215
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-mark-controls-as-safe-controls"></a>方法: コントロールを安全なコントロールとしてマークする
  セキュリティを SharePoint と区別するスクリプト インジェクションから保護されている Web コントロールがない Web コントロールです。 コントロールを保護または*安全なコントロール*、信頼されていないユーザーによってアクセスされることができます。 SharePoint プロジェクト項目のまたは安全なコントロール エントリ プロパティでも安全だとコントロールをマークすることができます、**パッケージ デザイナー**パッケージにアセンブリを追加するとします。 詳細については、次のトピックを参照してください。  
  
 [web.config ファイルの設定の変更](http://go.microsoft.com/fwlink/?LinkId=178965)と[Web パーツ アセンブリを登録する安全なコントロールとして](http://go.microsoft.com/fwlink/?LinkId=171013)です。  
  
> [!IMPORTANT]  
>  これらの手順では、わかりやすくするためです。 マークは、安全なは、セキュリティで保護されることがわかっている場合にのみ制御します。  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>安全なコントロール エントリ プロパティで安全なコントロールの指定  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>コントロールを安全なまたは安全なコントロール エントリ プロパティに安全でないとマークするには  
  
1.  プロジェクトを視覚的 Web パーツには、SharePoint ソリューションを作成します。  
  
2.  Web パーツに 2 つのコントロールを追加します。 テキスト ボックスとボタン。 それぞれが既定値は、TextBox1 と Button1、名前のままにします。  
  
3.  Web パーツの 2 つのエントリを追加**安全なコントロール エントリ**プロパティです。 これを行うには、選択、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) ボタンを**安全なコントロール エントリ**内のプロパティ**プロパティ**ウィンドウです。  
  
     **安全なコントロール エントリ** ダイアログ ボックスが表示されます。  
  
4.  **安全なコントロール エントリ** ダイアログ ボックスで、選択、**追加** ボタンを 2 つの安全なコントロール エントリを追加するには、2 回、**メンバー**ペイン: ボタンとテキスト ボックスのいずれかのいずれか。  
  
5.  最初の安全なコントロール エントリを選択しの値を変更し、その**セーフ**プロパティを**False**、その**型名**プロパティを**Button1**、およびその**スクリプトに対して安全**プロパティを**False**です。  
  
     この手順では、安全でないコントロールとしてボタン コントロールを識別します。  
  
6.  一覧に 2 つ目の安全なコントロール エントリを選択します。 値を受け入れ、**セーフ**プロパティとして**True**設定とその**型名**プロパティを**TextBox1**とその**セーフであります。スクリプトに対して**プロパティを**True**です。  
  
     テキスト ボックス コントロールがスクリプト インジェクションを安全なコントロールとしてマークされているようになりました。  
  
7.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>パッケージ デザイナーでの安全なコントロールをマークします。  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>コントロール セーフまたはパッケージ デザイナーで安全でないとマークするのには  
  
1.  プロジェクトを視覚的 Web パーツには、SharePoint ソリューションを作成します。  
  
2.  Web パーツに 2 つのコントロールを追加します。 テキスト ボックスとボタン。 それぞれが既定値は、TextBox1 と Button1、名前のままにします。  
  
     後で使用されているため、コントロールの名前空間を書き留めておきます。  
  
3.  メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、プロジェクトをビルドします。  
  
4.  別の SharePoint ソリューションを作成します。  
  
5.  **ソリューション エクスプ ローラー**Package.Package ファイルのショートカット メニューを開きを選択し、**開く**を開くには、**パッケージ デザイナー**です。  
  
6.  **パッケージ デザイナー**、選択、**詳細**タブです。  
  
7.  **追加アセンブリ**を選択、**追加**ボタンをクリックし、**既存のアセンブリを追加**一覧からです。  
  
8.  **既存のアセンブリの追加** ダイアログ ボックスで、省略記号ボタンを選択 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) ボタンを**ソース パス**です。  
  
9. 手順 1. で作成した SharePoint ソリューションからアセンブリを選択し、、**開く**ボタンをクリックします。  
  
10. この例では、選択したままに、**配置ターゲット**GlobalAssemblyCache としてオプション。  
  
     この手順では、アセンブリをグローバル アセンブリ キャッシュ (GAC) システムに配置します。 Web アプリケーション (ビン) フォルダーに配置するアセンブリを実行する場合に、そのオプションを選択します。 詳細については、次を参照してください。 [SharePoint Foundation の Web パーツを配置する](http://go.microsoft.com/fwlink/?LinkId=177509)です。  
  
11. **安全なコントロール**ボックスで、選択、**ここをクリックして、新しい項目を追加する**ボタンをクリックします。  
  
12. 次の表から、プロパティの値を入力します。  
  
    |プロパティ名|値|  
    |-------------------|-----------|  
    |名前空間|コントロールは、完全修飾名前空間など**BdcModelProject1.VisualWebPart1**です。|  
    |型の名前|ボタン 1|  
    |アセンブリ名|厳密なアセンブリ名など、: Microsoft.Office.SharePoint.ClientExtensions、バージョン 14.0.0.0、Culture = neutral, PublicKeyToken = 71e9bce111e9429c を = です。|  
    |セーフ|クリア、**セーフ**チェック ボックスをオンします。|  
    |スクリプトに対して安全|ままにして、**スクリプトに対して安全**チェック ボックスをオフします。|  
  
    > [!NOTE]  
    >  **アセンブリ名**アセンブリを使用して追加の値、 **[詳細設定]**のタブ、**パッケージ デザイナー**できませんトークンをする必要があります、厳密な名前付きのアセンブリ。 詳しくは、「[厳密な名前付きアセンブリの作成と使用](http://go.microsoft.com/fwlink/?LinkId=177513)」をご覧ください。  
  
13. 別の安全なコントロール エントリを作成する、Tab キーを選択します。  
  
14. 選択、**ここをクリックして、新しい項目を追加する**を再度クリックします。  
  
15. 次の表から、プロパティの値を入力します。  
  
    |プロパティ名|値|  
    |-------------------|-----------|  
    |名前空間|コントロールは、完全修飾名前空間など**BdcModelProject1.VisualWebPart1**です。|  
    |型の名前|TextBox1|  
    |アセンブリ名|厳密なアセンブリ名など、: Microsoft.Office.SharePoint.ClientExtensions、バージョン 14.0.0.0、Culture = neutral, PublicKeyToken = 71e9bce111e9429c を = です。|  
    |セーフ|選択、**セーフ**チェック ボックスをオンします。|  
    |スクリプトに対して安全|選択、**スクリプトに対して安全**チェック ボックスをオンします。|  
  
16. Tab キーを選択し、[、 **OK** ] ダイアログ ボックスを閉じるボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [パッケージとプロジェクト アイテムの展開情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  