---
title: "設定のカテゴリを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイルの設定を使用して、カテゴリを作成します。"
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 39
caps.handback.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
---
# 設定のカテゴリを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルは、Visual Studio の設定のカテゴリを作成し、値を保存し、設定ファイルから値を復元する使用します。 カテゴリの設定は、カスタム設定「ポイント」; として表示される関連するプロパティのグループつまりのチェック ボックスと、 **インポートおよびエクスポート設定** ウィザード。 \(\[あります、 **ツール** メニュー\)。 設定を保存または復元をカテゴリとして、個々 の設定は、ウィザードには表示されません。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 派生することで、カテゴリの設定を作成する、 <xref:Microsoft.VisualStudio.Shell.DialogPage> クラスです。  
  
 このチュートリアルを開始するの最初のセクションを最初に完了する必要があります [オプション ページを作成します。](../extensibility/creating-an-options-page.md)します。 結果として得られるオプションのプロパティ グリッドを確認し、カテゴリのプロパティを変更することができます。 プロパティのカテゴリの設定ファイルを保存した後は、プロパティ値を格納する方法を表示するファイルを調べます。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## 設定のカテゴリを作成します。  
 このセクションでは、カスタム設定ポイントを使用するを保存し、\[設定\] カテゴリの値を復元します。  
  
#### 設定のカテゴリを作成するには  
  
1.  完了、 [オプション ページを作成します。](../extensibility/creating-an-options-page.md)です。  
  
2.  VSPackage.resx ファイルを開き、次の 3 つの文字列リソースを追加します。  
  
    |名前|値|  
    |--------|-------|  
    |106|\[カテゴリ|  
    |107|設定|  
    |108|OptionInteger と OptionFloat|  
  
     これは、その名前、カテゴリの"My Category"、オブジェクト"My Settings"、およびカテゴリの説明"OptionInteger と OptionFloat"で、リソースを作成します。  
  
    > [!NOTE]
    >  これら 3 つのカテゴリの名前だけがインポートとエクスポートの設定ウィザードで表示されません。  
  
3.  MyToolsOptionsPackage.cs で追加、 `float` という名前のプロパティ `OptionFloat` に、 `OptionPageGrid` クラスでは次の例に示すようにします。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid` "My Category"を今すぐという名前のカテゴリには 2 つのプロパティの `OptionInteger` と `OptionFloat`です。  
  
4.  追加、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> に、 `MyToolsOptionsPackage` クラスし CategoryName"My Category"を付けます、ObjectName「個人の設定」を付けますおよび isToolsOptionPage を true に設定します。 対応する文字列リソース Id が前に作成するには、categoryResourceID、objectNameResourceID、および DescriptionResourceID を設定します。  
  
    ```c#  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示される **個人用のグリッド ページ** 整数と浮動小数点数の両方の値になりました。  
  
## 設定ファイルを確認します。  
 このセクションでは、プロパティのカテゴリの値を設定ファイルにエクスポートします。 ファイルを確認し、プロパティのカテゴリに値をインポートします。  
  
1.  F5 キーを押して、デバッグ モードで、プロジェクトを起動します。 これは、実験用インスタンスを起動します。  
  
2.  開いている、 **ツール\/オプション** ダイアログ。  
  
3.  左側のウィンドウのツリー ビューで、展開 **My Category** \] をクリックし、 **個人用のグリッド ページ**します。  
  
4.  値を変更 **OptionFloat** 3.1416 へと **OptionInteger** 12 にします。**\[OK\]** をクリックします。  
  
5.  **\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** を選択します。  
  
     **インポートおよびエクスポート設定** ウィザードが表示されます。  
  
6.  確認 **選択された環境設定をエクスポート** クリックして選択すると、 **次**します。  
  
     **エクスポートするには、\[設定の選択** ページが表示されます。  
  
7.  クリックして **設定**します。  
  
     **説明** 変更 **OptionInteger と OptionFloat**します。  
  
8.  確認して **個人の設定** が唯一のカテゴリを選択し、\[ **次**します。  
  
     **名前、設定ファイル** ページが表示されます。  
  
9. 新しい設定ファイルに名前を `MySettings.vssettings` し、適切なディレクトリに保存します。**\[完了\]** をクリックします。  
  
     **エクスポートの完了** \] ページで、設定が正常にエクスポートされたことを報告します。  
  
10. **ファイル** \] メニューをポイント **開く**, 、\] をクリックし、 **ファイル**します。 検索 `MySettings.vssettings` し、開きます。  
  
     \(、Guid は異なります\)、ファイルの次のセクションでエクスポートしたプロパティのカテゴリが表示されます。  
  
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
  
     カテゴリ名の後に、オブジェクト名にアンダー スコアを追加して、すべてのカテゴリの名前を生成することに注意してください。 OptionFloat と OptionInteger は、\[カテゴリで、そのエクスポート値と共に表示されます。  
  
11. これを変更することがなく、設定ファイルを閉じます。  
  
12. **ツール** \] メニューのをクリックして **オプション**, 、展開 **My Category**, 、\] をクリックして **個人用のグリッド ページ** の値を変更し、 **OptionFloat** 1.0 と **OptionInteger** を 1 にします。**\[OK\]** をクリックします。  
  
13. **ツール** \] メニューのをクリックして **インポートおよびエクスポート設定**, を選択 **選択された環境設定をインポート**, 、順にクリック **次**します。  
  
     **現在の設定の保存** ページが表示されます。  
  
14. 選択 **残念ですが、新しい設定をインポート** \] をクリックし、 **次**します。  
  
     **インポートする設定コレクションの選択** ページが表示されます。  
  
15. 選択、 `MySettings.vssettings` ファイルで、 **個人の設定** ツリー ビューのノードです。 ツリー ビューで、ファイルが表示されない場合はクリックして **参照** だとします。**\[次へ\]** をクリックします。  
  
     **インポートするには、\[設定の選択** \] ダイアログ ボックスが表示されます。  
  
16. 確認して **個人の設定** クリックして選択すると、 **完了**します。 ときに、 **インポートの完了** ページが表示されたら、クリックして **閉じる**します。  
  
17. **ツール** \] メニューのをクリックして **オプション**, 、展開 **My Category**, 、\] をクリックして **個人用のグリッド ページ** プロパティ カテゴリの値が復元されたことを確認します。