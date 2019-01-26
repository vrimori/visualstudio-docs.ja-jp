---
title: '方法: 安全なコントロールとしてマークが制御 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d3f0ff39658aca76318174143da52e17594ace24
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875459"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>方法: 安全なコントロールとしてマーク コントロール
  セキュリティを SharePoint は、スクリプト インジェクションから保護されている Web コントロールとはない Web コントロールの間で区別されます。 コントロールを保護または*安全なコントロール*、信頼されていないユーザーによってアクセスされることができます。 SharePoint プロジェクト アイテムのまたは安全なコントロール エントリ プロパティでも安全だとコントロールをマークすることができます、**パッケージ デザイナー**パッケージにアセンブリを追加するとします。 詳細については、次のトピックを参照してください。  
  
 [web.config ファイル設定の変更](http://go.microsoft.com/fwlink/?LinkId=178965)と[安全なコントロールとして、Web パーツ アセンブリを登録する](http://go.microsoft.com/fwlink/?LinkId=171013)します。  
  
> [!IMPORTANT]  
>  これらの手順では、例示を目的としてです。 マークは、安全なは、セキュリティで保護されることがわかっている場合にのみ制御します。  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>安全なコントロール エントリのプロパティで安全なコントロールの指定  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Safe または安全なコントロール エントリのプロパティでアンセーフとしてコントロールをマークするには
  
1.  視覚的 Web パーツ プロジェクトには、SharePoint ソリューションを作成します。  
  
2.  Web パーツに 2 つのコントロールを追加します。 テキスト ボックスとボタン。 それぞれの既定値は、TextBox1 および Button1、名前のままにします。  
  
3.  Web パーツの 2 つのエントリを追加**安全なコントロール エントリ**プロパティ。 これを行うには、省略記号をクリックします (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) ボタンの横に、**安全なコントロール エントリ**プロパティ**プロパティ**ウィンドウ。  
  
     **安全なコントロール エントリ** ダイアログ ボックスが表示されます。  
  
4.  **安全なコントロール エントリ** ダイアログ ボックスで、選択、**追加**ボタンを 2 つの安全なコントロール エントリを追加するには、2 回、**メンバー**ペイン: 1 つは、ボタン、テキスト ボックスのいずれか。  
  
5.  最初の安全なコントロール エントリを選択しの値を変更し、その**セーフ**プロパティを**False**その**型名**プロパティを**Button1**、およびその**スクリプトに対して安全**プロパティを**False**します。  
  
     この手順では、安全でないコントロールとしてボタン コントロールを識別します。  
  
6.  一覧で、2 番目の安全なコントロール エントリを選択します。 値をそのままその**セーフ**プロパティとして**True**設定とその**型名**プロパティを**TextBox1**とその**セーフスクリプトに対して**プロパティを**True**します。  
  
     テキスト ボックス コントロールがスクリプト インジェクションに対する安全なコントロールとしてマークされているようになりました。  
  
7.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>パッケージ デザイナーでの安全なコントロールをマークします。  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>マークするには、コントロールを安全またはパッケージ デザイナーで安全でないです。
  
1.  視覚的 Web パーツ プロジェクトには、SharePoint ソリューションを作成します。  
  
2.  Web パーツに 2 つのコントロールを追加します。 テキスト ボックスとボタン。 それぞれの既定値は、TextBox1 および Button1、名前のままにします。  
  
     後で使用されているので、コントロールの名前空間を書き留めておきます。  
  
3.  メニュー バーで、**ビルド** > **ソリューションのビルド**プロジェクトをビルドします。  
  
4.  別の SharePoint ソリューションを作成します。  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 *Package.Package*ファイルを選び、**開く**を開く、**パッケージ デザイナー**.  
  
6.  **パッケージ デザイナー**、選択、**詳細**タブ。  
  
7.  **追加アセンブリ**、選択、**追加**ボタンをクリックし、**既存アセンブリの追加**一覧から。  
  
8.  **既存アセンブリの追加** ダイアログ ボックスで、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) ボタンの横に**ソース パス**します。  
  
9. 手順 1. で作成した SharePoint ソリューションからアセンブリを選択し、、**オープン**ボタンをクリックします。  
  
10. この例では、選択したままに、**配置ターゲット**GlobalAssemblyCache としてオプション。  
  
     この手順では、アセンブリをグローバル アセンブリ キャッシュ (GAC) システムに配置します。 Web アプリケーション (ビン) フォルダーを展開するアセンブリを実行する場合に、そのオプションを選択します。 詳細については、次を参照してください。 [SharePoint Foundation の Web パーツを配置する](http://go.microsoft.com/fwlink/?LinkId=177509)します。  
  
11. **安全なコントロール**ボックスで、選択、**ここをクリックすると、新しい項目を追加する**ボタンをクリックします。  
  
12. 次の表から、プロパティの値を入力します。  
  
    |プロパティ名|[値]|  
    |-------------------|-----------|  
    |名前空間|コントロールの完全修飾名前空間など**BdcModelProject1.VisualWebPart1**します。|  
    |型の名前|ボタン 1|  
    |アセンブリ名|厳密なアセンブリ名など。Microsoft.Office.SharePoint.ClientExtensions、バージョン 14.0.0.0、Culture = neutral, PublicKeyToken = 71e9bce111e9429c を = です。|  
    |Safe|クリア、**セーフ**チェック ボックスをオンします。|  
    |スクリプトに対して安全|ままに、**スクリプトに対して安全**チェック ボックスをクリアします。|  
  
    > [!NOTE]  
    >  **アセンブリ名**アセンブリを使用して追加の値、**詳細**のタブ、**パッケージ デザイナー**ことはできません、トークンであることをする必要があります、厳密な名前付きのアセンブリ。 詳しくは、「[厳密な名前付きアセンブリの作成と使用](http://go.microsoft.com/fwlink/?LinkId=177513)」をご覧ください。  
  
13. 選択、**タブ**別の安全なコントロール エントリを作成するキー。  
  
14. 選択、**ここをクリックすると、新しい項目を追加する**もう一度ボタンをクリックします。  
  
15. 次の表から、プロパティの値を入力します。  
  
    |プロパティ名|[値]|  
    |-------------------|-----------|  
    |名前空間|コントロールの完全修飾名前空間など**BdcModelProject1.VisualWebPart1**します。|  
    |型の名前|TextBox1|  
    |アセンブリ名|厳密なアセンブリ名など。Microsoft.Office.SharePoint.ClientExtensions、バージョン 14.0.0.0、Culture = neutral, PublicKeyToken = 71e9bce111e9429c を = です。|  
    |Safe|選択、**セーフ**チェック ボックスをオンします。|  
    |スクリプトに対して安全|選択、**スクリプトに対して安全**チェック ボックスをオンします。|  
  
16. 選択、**タブ**キーを選び、 **OK**ボタンをクリックしてダイアログ ボックスを閉じます。  
  
## <a name="see-also"></a>関連項目
 [プロジェクト項目でパッケージ化と配置の情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [パッケージと SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
