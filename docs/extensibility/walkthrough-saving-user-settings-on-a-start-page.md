---
title: 'チュートリアル: スタート ページでユーザー設定の保存 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa57fb8c4e0c85ff7a9c1b258f1c326a241442c3
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566718"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>チュートリアル: [スタート] ページのユーザー設定を保存します。
スタート ページのユーザー設定を永続化することができます。 このチュートリアルでは、ユーザーが、ボタンをクリックするし、開始ページが読み込まれるたびに、その設定を取得し、設定をレジストリに保存するコントロールを作成できます。 スタート ページ プロジェクト テンプレートには、カスタマイズ可能なユーザー コントロールが含まれています。 既定のスタート ページの XAML は、そのコントロールを呼び出すため、スタート ページ自体を変更する必要はありません。  
  
 このチュートリアルでインスタンス化される設定ストアのインスタンスである、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>インターフェイスでは、読み取りし、が呼び出されると、次のレジストリの場所に書き込み: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName >**  
  
 設定ストアが読み取りし、書き込みに Visual Studio の実験用インスタンスで実行されている、 **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<CollectionName >。**  
  
 設定を保持する方法の詳細については、次を参照してください。 [Extending User Settings and オプション](../extensibility/extending-user-settings-and-options.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
> [!NOTE]
>  このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
>   
>  使用して、スタート ページ プロジェクト テンプレートをダウンロードする**拡張機能マネージャー**します。  
  
## <a name="setting-up-the-project"></a>プロジェクトの設定  
  
### <a name="to-configure-the-project-for-this-walkthrough"></a>このチュートリアルのプロジェクトを構成するには  
  
1.  スタート ページ プロジェクトを作成する」の説明に従って[カスタム スタート ページを作成する](creating-a-custom-start-page.md)します。 プロジェクトに名前を**SaveMySettings**します。  
  
2.  **ソリューション エクスプ ローラー**、StartPageControl プロジェクトに次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  開いている*MyControl.xaml*します。  
  
4.  XAML ウィンドウの最上位から<xref:System.Windows.Controls.UserControl>要素の定義、名前空間宣言の後、次のイベント宣言を追加します。  
  
    ```xml 
    Loaded="OnLoaded"  
    ```  
  
5.  デザイン ペインで、コントロールの主な領域をクリックし、キーを押します**削除**します。  
  
     この手順を削除、<xref:System.Windows.Controls.Border>要素と、その中のすべてしレベル上位のみを残します<xref:System.Windows.Controls.Grid>要素。  
  
6.  **ツールボックス**、ドラッグ、<xref:System.Windows.Controls.StackPanel>グリッド コントロール。  
  
7.  ここで、ドラッグ、 <xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.TextBox>、ボタンをクリックし、 <xref:System.Windows.Controls.StackPanel>。  
  
8.  追加、 **X:name**属性、<xref:System.Windows.Controls.TextBox>と`Click`イベントを<xref:System.Windows.Controls.Button>次の例のようにします。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implement-the-user-control"></a>ユーザー コントロールを実装します。  
  
### <a name="to-implement-the-user-control"></a>ユーザー コントロールを実装するには  
  
1.  XAML ウィンドウで右クリックし、`Click`の属性、<xref:System.Windows.Controls.Button>要素、およびクリック**イベント ハンドラーへ移動**します。  
  
     この手順が開きます*MyControl.xaml.cs*、スタブのハンドラーを作成し、`Button_Click`イベント。  
  
2.  次の追加`using`ステートメント ファイルの先頭にします。  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  追加のプライベート`SettingsStore`プロパティは、次の例に示すようにします。  
  
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
  
     このプロパティは、まずへの参照を取得します。、<xref:EnvDTE80.DTE2>インターフェイスから、オートメーション オブジェクト モデルを含む、<xref:System.Windows.FrameworkElement.DataContext%2A>のユーザー コントロール、および、使用のインスタンスを取得する DTE、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>インターフェイス。 そのインスタンスを使用して現在のユーザー設定を返します。  
  
4.  入力、`Button_Click`イベントとして次のとおりです。  
  
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
  
     これは、レジストリ内の"MySettings"コレクション内の"MySetting"フィールドにテキスト ボックスのコンテンツを書き込みます。 コレクションが存在しない場合は作成されます。  
  
5.  次のハンドラーを追加、`OnLoaded`ユーザー コントロールのイベント。  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     このコードは、テキスト ボックスのテキストを"MySetting"の現在の値に設定します。  
  
6.  ユーザー コントロールをビルドします。  
  
7.  **ソリューション エクスプ ローラー**オープン*source.extension.vsixmanifest*します。  
  
8.  マニフェストのエディターで次のように設定します。**製品名**に**個人用設定のスタート ページの保存**します。  
  
     表示するには、この機能はスタート ページの名前を設定、**スタート ページのカスタマイズ**の一覧で、**オプション** ダイアログ ボックス。  
  
9. ビルド*StartPage.xaml*します。  
  
## <a name="test-the-control"></a>コントロールをテストします。  
  
### <a name="to-test-the-user-control"></a>ユーザー コントロールをテストするには  
  
1.  **F5**キーを押します。  
  
     Visual Studio の実験用インスタンスを開きます。  
  
2.  実験用インスタンスでは、上、**ツール** メニューのをクリックして**オプション**します。  
  
3.  **環境**ノード、をクリックして**スタートアップ**、[、**スタート ページのカスタマイズ**一覧で、 **[インストールされている拡張機能] ページの保存個人用設定を開始]**.  
  
     **[OK]** をクリックします。  
  
4.  場合は、開いているし、[スタート ページを閉じ、**ビュー** ] メニューのをクリックして**スタート ページ**します。  
  
5.  [スタート] ページで、をクリックして、 **MyControl**タブ。  
  
6.  テキスト ボックスに「 **Cat**、 をクリックし、**個人用設定の保存**します。  
  
7.  スタート ページを閉じて、再び開きます。  
  
     "Cat"という単語は、テキスト ボックスに表示する必要があります。  
  
8.  "Cat"という単語を"Dog"ワードに置き換えます。 ボタンをクリックしてしないでください。  
  
9. スタート ページを閉じて、再び開きます。  
  
     場合でも、Visual Studio 自体を終了するまで、終了は、設定、Visual Studio は、メモリ内のツール ウィンドウを保持しているためにを保存するしなかった場合でも、テキスト ボックスに単語"Dog"が表示されます。  
  
10. Visual Studio の実験用インスタンスを終了します。  
  
11. キーを押して**F5**実験用インスタンスを再開します。  
  
12. "Cat"という単語は、テキスト ボックスに表示する必要があります。  
  
## <a name="next-steps"></a>次の手順  
 保存し、別のイベント ハンドラーから異なる値を取得および設定を使用して任意の数のカスタム設定を取得するには、このユーザー コントロールを変更することができます、`SettingsStore`プロパティ。 異なるを使用する限り`propertyName`呼び出しごとにパラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>値は、レジストリで互いを上書きしないでください。  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Visual Studio のコマンドをスタート ページに追加します。](../extensibility/adding-visual-studio-commands-to-a-start-page.md)