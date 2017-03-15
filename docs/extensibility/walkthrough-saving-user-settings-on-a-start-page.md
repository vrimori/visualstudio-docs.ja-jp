---
title: "チュートリアル: [スタート] ページのユーザー設定の保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 1bf8a313898f9c12312beedb31238fb74e1a56a8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>チュートリアル: [スタート] ページのユーザー設定の保存
スタート ページのユーザー設定を保持できます。 このチュートリアルでは、ユーザーが、ボタンをクリックするし、開始ページが読み込まれるたびに、その設定を取得し、設定をレジストリに保存するコントロールを作成できます。 スタート ページのプロジェクト テンプレートには、カスタマイズ可能なユーザー コントロールが含まれています。 既定のスタート ページの XAML は、そのコントロールを呼び出すため、自体がスタート ページを変更する必要はありません。  
  
 このチュートリアルでインスタンス化設定ストアのインスタンスである、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>インタ フェースが読み取られてされが呼び出されると、次のレジストリ位置に書き込みます: HKCU\Software\Microsoft\VisualStudio\14.0\\*CollectionName* </xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>  
  
 Visual Studio の実験用インスタンスで実行されている設定ストアはに対する読み書き HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName します。*  
  
 設定を保存する方法の詳細については、次を参照してください。[ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
> [!NOTE]
>  このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
>   
>  使用して、[スタート] ページでプロジェクト テンプレートをダウンロードする**拡張機能マネージャー**します。  
  
## <a name="setting-up-the-project"></a>プロジェクトの設定  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>このチュートリアルのプロジェクトを構成するには  
  
1.  説明に従って、スタート ページのプロジェクトを作成[カスタム スタート ページを作成する](creating-a-custom-start-page.md)です。 プロジェクトに名前を**SaveMySettings**します。  
  
2.  **ソリューション エクスプ ローラー**、StartPageControl プロジェクトに次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  MyControl.xaml を開きます。  
  
4.  [XAML] ウィンドウの最上位レベルでから<xref:System.Windows.Controls.UserControl>要素の定義、名前空間宣言の後に次のイベント宣言を追加します</xref:System.Windows.Controls.UserControl>。  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  デザイン ペインで、コントロールの主な領域をクリックし、DEL キーを押します。  
  
     これにより、削除、<xref:System.Windows.Controls.Border>要素と、およびだけ、最上位レベルのリーフ内のすべての<xref:System.Windows.Controls.Grid>要素</xref:System.Windows.Controls.Grid></xref:System.Windows.Controls.Border>。  
  
6.  **ツールボックス**、ドラッグ、<xref:System.Windows.Controls.StackPanel>コントロールはグリッドにします</xref:System.Windows.Controls.StackPanel>。  
  
7.  ここで、ドラッグ、 <xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.TextBox>、および<xref:System.Windows.Controls.StackPanel></xref:System.Windows.Controls.StackPanel>ボタン</xref:System.Windows.Controls.TextBox></xref:System.Windows.Controls.TextBlock>。  
  
8.  追加、 **X:name**属性を<xref:System.Windows.Controls.TextBox>、および`Click`イベントを<xref:System.Windows.Controls.Button>、次の例のように、</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.TextBox> 。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>ユーザー コントロールを実装します。  
  
#### <a name="to-implement-the-user-control"></a>ユーザー コントロールを実装するには  
  
1.  [XAML] ウィンドウで右クリックし、`Click`の属性、<xref:System.Windows.Controls.Button>要素、およびクリック**イベント ハンドラーへ移動**</xref:System.Windows.Controls.Button>。  
  
     MyControl.xaml.cs を開き、用のスタブ ハンドラーを作成、`Button_Click`イベントです。  
  
2.  次の追加`using`ステートメントをファイルの先頭にします。  
  
     [!code-cs[StartPageDTE&#11;](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  追加のプライベート`SettingsStore`プロパティ、次の例で示したようにします。  
  
    ```c#  
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
  
     このプロパティは、まずへの参照を取得、<xref:EnvDTE80.DTE2>からオートメーション オブジェクト モデルを含むインターフェイス、<xref:System.Windows.FrameworkElement.DataContext%2A>のユーザー コントロールとし、用途のインスタンスを取得する DTE の<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager></xref:System.Windows.FrameworkElement.DataContext%2A></xref:EnvDTE80.DTE2>。 そのインスタンスを使用して現在のユーザー設定を返します。  
  
4.  入力、`Button_Click`イベントを次のようにします。  
  
    ```c#  
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
  
    ```c#  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     これにより、テキスト ボックスのテキストが"MySetting"の現在の値に設定されます。  
  
6.  ユーザー コントロールをビルドします。  
  
7.  **ソリューション エクスプ ローラー**source.extension.vsixmanifest を開きます。  
  
8.  マニフェスト エディターで次のように設定します。**製品名**に**個人用の設定の開始ページの保存**します。  
  
     表示するには、これの設定を開始 ページの名前、**スタート ページのカスタマイズ**リストに、**オプション** ダイアログ ボックス。  
  
9. StartPage.xaml をビルドします。  
  
## <a name="testing-the-control"></a>コントロールのテスト  
  
#### <a name="to-test-the-user-control"></a>ユーザー コントロールをテストするには  
  
1.  F5 キーを押します。  
  
     Visual Studio の実験用インスタンスが開きます。  
  
2.  実験用インスタンスで、**ツール** メニューのをクリックして**オプション**します。  
  
3.  **環境**] ノードをクリックして**スタートアップ**、[、**スタート ページのカスタマイズ**一覧で、[ **[インストールされている拡張機能] ページの保存個人用設定を開始]**します。  
  
     **[OK]** をクリックします。  
  
4.  開いて場合してから、スタート ページを閉じる、**ビュー**  メニューのをクリックして**スタート ページ**します。  
  
5.  スタート ページで、クリックして、 **MyControl**  タブをクリックします。  
  
6.  テキスト ボックスに入力**Cat**、クリックして**個人用設定の保存**します。  
  
7.  スタート ページを閉じて、再び開きます。  
  
     "Cat"という単語は、テキスト ボックスに表示する必要があります。  
  
8.  "Cat"という単語を単語"Dog"に置き換えます。 ボタンをクリックします。  
  
9. スタート ページを閉じて、再び開きます。  
  
     設定が保存されなかった場合でも、テキスト ボックスに単語"Dog"が表示されます。 これは Visual Studio 自体が閉じられるまで、閉じた場合でも、Visual Studio は、メモリ内のツール ウィンドウを保持しているためです。  
  
10. Visual Studio の実験用インスタンスを終了します。  
  
11. F5 キーを押して実験用インスタンスを再度開きます。  
  
12. "Cat"という単語は、テキスト ボックスに表示する必要があります。  
  
## <a name="next-steps"></a>次の手順  
 保存および取得および設定する値が異なる別のイベント ハンドラーを使用して、任意の数のカスタム設定を取得するには、このユーザー コントロールを変更することができます、`SettingsStore`プロパティです。 異なるを使用する限り、`propertyName`呼び出しごとにパラメーター <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>、値は上書きされません相互レジストリ</xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>。  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE80.DTE2?displayProperty=fullName></xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Visual Studio のコマンドをスタート ページに追加します。](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
