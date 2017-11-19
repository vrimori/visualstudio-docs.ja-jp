---
title: "チュートリアル: スタート ページ上のユーザー設定の保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a7d8649e0d8cf83650da58386901e638ec14a2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>チュートリアル: スタート ページ上のユーザー設定の保存
スタート ページのユーザー設定を保持できます。 このチュートリアルでは、ユーザーが、ボタンをクリックするし、開始ページが読み込まれるたびに、その設定を取得し、設定をレジストリに保存するコントロールを作成できます。 スタート ページ プロジェクト テンプレートには、カスタマイズ可能なユーザー コントロールが含まれています。 既定のスタート ページの XAML は、そのコントロールを呼び出すためがありません自体スタート ページを変更します。  
  
 このチュートリアルでインスタンス化設定ストアのインスタンスである、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>インターフェイスでは、読み取り、書き込み、次のレジストリの場所が呼び出されると: HKCU\Software\Microsoft\VisualStudio\14.0\\ *CollectionName*  
  
 Visual Studio の実験用インスタンスで実行されている設定ストアに対する読み書き HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName です。*  
  
 設定を保持する方法の詳細については、次を参照してください。[ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
> [!NOTE]
>  このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
>   
>  使用して、スタート ページ プロジェクト テンプレートをダウンロードする**拡張機能マネージャー**です。  
  
## <a name="setting-up-the-project"></a>プロジェクトの設定  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>このチュートリアルのプロジェクトを構成するには  
  
1.  スタート ページ プロジェクトの作成」の説明に従って[カスタム スタート ページを作成する](creating-a-custom-start-page.md)です。 プロジェクトに名前を**SaveMySettings**です。  
  
2.  **ソリューション エクスプ ローラー**、StartPageControl プロジェクトに次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  MyControl.xaml を開きます。  
  
4.  XAML ウィンドウの最上位から<xref:System.Windows.Controls.UserControl>要素の定義、名前空間宣言の後、次のイベントの宣言を追加します。  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  デザイン ペインで、コントロールの主な領域をクリックし、DEL キーを押します。  
  
     これにより、削除、<xref:System.Windows.Controls.Border>要素と、およびリーフだけ、最上位にあるすべて<xref:System.Windows.Controls.Grid>要素。  
  
6.  **ツールボックス**、ドラッグ、<xref:System.Windows.Controls.StackPanel>コントロールはグリッドにします。  
  
7.  ここで、ドラッグ、 <xref:System.Windows.Controls.TextBlock>、<xref:System.Windows.Controls.TextBox>とにボタン、<xref:System.Windows.Controls.StackPanel>です。  
  
8.  追加、 **X:name**属性を<xref:System.Windows.Controls.TextBox>、および`Click`イベントを<xref:System.Windows.Controls.Button>次の例で示すように、します。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>ユーザー コントロールを実装します。  
  
#### <a name="to-implement-the-user-control"></a>ユーザー コントロールを実装するには  
  
1.  XAML ウィンドウで右クリックし、`Click`の属性、<xref:System.Windows.Controls.Button>要素、およびクリック**イベント ハンドラーへ移動**です。  
  
     MyControl.xaml.cs が開きのスタブ ハンドラーを作成、`Button_Click`イベント。  
  
2.  次の追加`using`ステートメントをファイルの先頭にします。  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  プライベートの追加`SettingsStore`プロパティ、次の例で示すようにします。  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     このプロパティは、まずへの参照を取得、<xref:EnvDTE80.DTE2>インターフェイスで、オートメーション オブジェクト モデルが含まれています、<xref:System.Windows.FrameworkElement.DataContext%2A>のユーザー コントロール、および、使用される DTE のインスタンスを取得する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>インターフェイスです。 そのインスタンスを使用して現在のユーザー設定を返します。  
  
4.  入力、`Button_Click`次のようにイベント。  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     これは、レジストリ内の「設定」コレクション内の"MySetting"フィールドにテキスト ボックスの内容を書き込みます。 コレクションが存在しない場合は作成されます。  
  
5.  次のハンドラーを追加、`OnLoaded`ユーザー コントロールのイベントです。  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     これは、"MySetting"の現在の値をテキスト ボックスのテキストを設定します。  
  
6.  ユーザー コントロールをビルドします。  
  
7.  **ソリューション エクスプ ローラー**source.extension.vsixmanifest を開きます。  
  
8.  マニフェスト エディターで、次のように設定します。 **Product Name**に**個人用設定の開始ページの保存**です。  
  
     スタート ページの名前で表示されている設定、**スタート ページのカスタマイズ**一覧に、**オプション** ダイアログ ボックス。  
  
9. StartPage.xaml をビルドします。  
  
## <a name="testing-the-control"></a>コントロールのテスト  
  
#### <a name="to-test-the-user-control"></a>ユーザー コントロールをテストするには  
  
1.  F5 キーを押します。  
  
     Visual Studio の実験用インスタンスが開きます。  
  
2.  実験用インスタンスの上、**ツール** メニューのをクリックして**オプション**です。  
  
3.  **環境**] ノードをクリックして**スタートアップ**、[、**スタート ページのカスタマイズ**一覧で、[ **[インストールされている拡張機能] 保存個人用設定を開始] ページ**.  
  
     **[OK]** をクリックします。  
  
4.  場合は、開いているし、[スタート ページを閉じ、**ビュー** ] メニューのをクリックして**スタート ページ**です。  
  
5.  [スタート] ページで、をクリックして、 **MyControl**タブです。  
  
6.  テキスト ボックスで、次のように入力します。 **Cat**、クリックして**個人用設定の保存**です。  
  
7.  スタート ページを閉じて、再び開きます。  
  
     "Cat"という単語がテキスト ボックスに表示されます。  
  
8.  "Cat"という単語を単語"Dog"に置き換えます。 ボタンをクリックしてしないでください。  
  
9. スタート ページを閉じて、再び開きます。  
  
     設定が保存されなかった場合でも、テキスト ボックスで word"および Dog"が表示されます。 これは Visual Studio 自体が閉じられるまで、閉じた場合でも、Visual Studio ツール ウィンドウをメモリに保持されているためです。  
  
10. Visual Studio の実験用インスタンスを終了します。  
  
11. F5 キーを押して、実験用インスタンスを再度開きます。  
  
12. "Cat"という単語がテキスト ボックスに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 保存および取得および設定する値が異なる別のイベント ハンドラーを使用して、任意の数のカスタム設定を取得するには、このユーザー コントロールを変更することができます、`SettingsStore`プロパティです。 異なるを使用する限り`propertyName`呼び出しごとにパラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>値は上書きされません互いのレジストリにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Visual Studio コマンドのスタート ページへの追加](../extensibility/adding-visual-studio-commands-to-a-start-page.md)