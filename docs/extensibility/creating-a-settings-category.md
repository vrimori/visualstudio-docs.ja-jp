---
title: 設定のカテゴリを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22a625466dd8a94ba1dbe67ef6f05bec68954d2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-settings-category"></a>設定のカテゴリを作成します。
このチュートリアルでは、Visual Studio の設定のカテゴリを作成し、使用して値を保存および設定ファイルから値を復元します。 設定のカテゴリは「カスタム設定ポイント」; として表示される関連するプロパティのグループつまりのチェック ボックスと、**インポートおよびエクスポート設定**ウィザード。 (上で見つけられる、**ツール**メニューです)。設定が保存または復元をカテゴリとして、個々 の設定は、ウィザードでは表示されません。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 派生することで、設定のカテゴリを作成する、<xref:Microsoft.VisualStudio.Shell.DialogPage>クラスです。  
  
 このチュートリアルを開始するの最初のセクションを完了する必要がありますまず[オプション ページを作成する](../extensibility/creating-an-options-page.md)です。 結果として得られるオプションのプロパティ グリッドを確認し、カテゴリのプロパティを変更することができます。 プロパティのカテゴリの設定ファイルを保存した後は、プロパティの値を格納する方法を参照してください。 ファイルを確認します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-settings-category"></a>設定のカテゴリを作成します。  
 このセクションでは、カスタム設定ポイントを使用するを保存し、[設定] カテゴリの値を復元します。  
  
#### <a name="to-create-a-settings-category"></a>設定のカテゴリを作成するには  
  
1.  完了、[オプション ページを作成する](../extensibility/creating-an-options-page.md)です。  
  
2.  VSPackage.resx ファイルを開き、これらの 3 つの文字列リソースを追加します。  
  
    |名前|[値]|  
    |----------|-----------|  
    |106|カテゴリ|  
    |107|自分の設定|  
    |108|OptionInteger と OptionFloat|  
  
     これは、その名前、カテゴリの「マイ カテゴリ」、オブジェクト「My 設定」、およびカテゴリの説明"OptionInteger と OptionFloat"で、リソースを作成します。  
  
    > [!NOTE]
    >  これらの 3 つのカテゴリの名前だけは、インポートとエクスポートの設定ウィザードには表示されません。  
  
3.  MyToolsOptionsPackage.cs で追加、`float`という名前のプロパティ`OptionFloat`を`OptionPageGrid`クラスに、次の例に示すようにします。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid` 「My カテゴリ」を今すぐという名前のカテゴリには 2 つのプロパティでは、`OptionInteger`と`OptionFloat`です。  
  
4.  追加、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>を`MyToolsOptionsPackage`クラスし CategoryName「My カテゴリ」を付けます、ObjectName My「設定」を付けますおよび isToolsOptionPage を true に設定します。 Id が以前に作成された、対応する文字列リソースを categoryResourceID、objectNameResourceID、および DescriptionResourceID を設定します。  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスでを参照する必要があります**個人用のグリッド ページ**整数と浮動小数点数の両方の値になりました。  
  
## <a name="examining-the-settings-file"></a>設定ファイルを確認します。  
 このセクションでは、プロパティのカテゴリの値を設定ファイルにエクスポートします。 ファイルを確認し、プロパティのカテゴリに値をインポートします。  
  
1.  F5 キーを押して、デバッグ モードで、プロジェクトを起動します。 これは、実験用インスタンスを起動します。  
  
2.  開く、**ツール/オプション**ダイアログ。  
  
3.  左側のウィンドウで、ツリー ビューで、展開**マイ カテゴリ** をクリックし、**個人用のグリッド ページ**です。  
  
4.  値を変更**OptionFloat** 3.1416 へと**OptionInteger** 12 にします。 **[OK]**をクリックします。  
  
5.  **ツール** メニューのをクリックして**インポートおよびエクスポート設定**です。  
  
     **インポートおよびエクスポート設定**ウィザードが表示されます。  
  
6.  確認**選択された環境設定をエクスポート**を選択して、をクリックして**[次へ]**です。  
  
     **設定のエクスポートを**ページが表示されます。  
  
7.  をクリックして**設定**です。  
  
     **説明**変更**OptionInteger と OptionFloat**です。  
  
8.  確認して**個人用設定**は、唯一のカテゴリを選択して、をクリックして**次**です。  
  
     **名前、設定ファイル**ページが表示されます。  
  
9. 新しい設定ファイルの名前を付けます`MySettings.vssettings`し、適切なディレクトリに保存します。 **[完了]**をクリックします。  
  
     **エクスポートの完了** ページで、設定が正常にエクスポートされたことを報告します。  
  
10. **ファイル** メニューのをポイント**開く**、順にクリック**ファイル**です。 検索`MySettings.vssettings`して開きます。  
  
     (、Guid は異なります)、ファイルの次のセクションでエクスポートしたプロパティのカテゴリを検索できます。  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     カテゴリ名の後に、オブジェクト名にアンダー スコアの追加により、すべてのカテゴリ名を生成することに注意してください。 OptionFloat と OptionInteger は、カテゴリで、そのエクスポートされた値と共に表示されます。  
  
11. これを変更することがなく、設定ファイルを閉じます。  
  
12. **ツール** メニューのをクリックして**オプション**、展開**マイ カテゴリ**、 をクリックして**個人用のグリッド ページ**しの値を変更して**OptionFloat** 1.0 と**OptionInteger**を 1 にします。 **[OK]**をクリックします。  
  
13. **ツール** メニューのをクリックして**インポートおよびエクスポート設定**を選択**選択された環境設定のインポート**、順にクリック**次へ**です。  
  
     **現在の設定を保存**ページが表示されます。  
  
14. 選択**いいえ、新しい設定をインポート** をクリックし、**次**です。  
  
     **インポートする設定コレクションの選択**ページが表示されます。  
  
15. 選択、`MySettings.vssettings`ファイルで、**個人用設定**ツリー ビューのノードです。 ツリー ビューで、ファイルが表示されない場合にクリックして**参照**だとします。 **[次へ]**をクリックします。  
  
     **[設定のインポートに**] ダイアログ ボックスが表示されます。  
  
16. 確認して**個人用設定**を選択して、をクリックして**完了**です。 ときに、**インポートの完了**ページが表示されたら、をクリックして**閉じる**です。  
  
17. **ツール** メニューのをクリックして**オプション**、展開**マイ カテゴリ**、 をクリックして**個人用のグリッド ページ**プロパティ カテゴリの値があることを確認してください復元されました。