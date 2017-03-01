---
title: "スタート ページにユーザー コントロールの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 69c2ff24616af373461de0cbf4456499db63f902
ms.lasthandoff: 02/22/2017

---
# <a name="adding-user-control-to-the-start-page"></a>スタート ページにユーザー コントロールを追加します。
このチュートリアルでは、カスタム スタート ページへの DLL 参照を追加する方法を示します。 例では、ソリューションにユーザー コントロールがユーザー コントロールをビルドし、スタート ページの .xaml ファイルからビルドされたアセンブリを参照を追加します。 新しいタブでは、基本的な Web ブラウザーとして機能するユーザー コントロールをホストします。  
  
 同じプロセスを使用すると、.xaml ファイルから呼び出すことができる任意のアセンブリを追加します。  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>ソリューションに WPF ユーザー コントロールの追加  
 最初に、Windows Presentation Foundation (WPF) ユーザー コントロールをスタート ページ ソリューションに追加します。  
  
1.  作成を開始 ページで作成したを使用して[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)です。  
  
2.  **ソリューション エクスプ ローラー**をソリューションを右クリックして、**追加**、 をクリックし、**新しいプロジェクト**します。  
  
3.  左側のウィンドウで、**新しいプロジェクト** ダイアログ ボックスで、いずれかを展開、 **Visual Basic**または**Visual C# の場合**ノード、およびクリック**Windows**します。 中央のウィンドウで  **WPF ユーザー コントロール ライブラリ**します。  
  
4.  コントロールの名前`WebUserControl` をクリックし、 **OK**します。  
  
## <a name="implementing-the-user-control"></a>ユーザー コントロールを実装します。  
 WPF ユーザー コントロールを実装するのには、XAML でユーザー インターフェイス (UI) を構築し、c# または他の .NET 言語でコードのイベントを書き込みます。  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>ユーザー コントロールの XAML を記述するには  
  
1.  ユーザー コントロールの XAML ファイルを開きます。 \<グリッド > 要素、コントロールに行の次の定義を追加します。  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  メイン`Grid`要素、次の新しい追加`Grid`要素は、Web アドレスと新しいアドレスを設定するためのボタンを入力するテキスト ボックスが含まれています。  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  次のフレームを最上位レベルに追加`Grid`要素直後に、 `Grid` button と textbox を含む要素です。  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  次の例では、ユーザー コントロールの完全な XAML を示します。  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>ユーザー コントロールの分離コード イベントの書き込み  
  
1.  XAML デザイナーで、ダブルクリック、**アドレスの設定**コントロールに追加 ボタンをクリックします。  
  
     UserControl1.cs ファイルは、コード エディターで開きます。  
  
2.  SetButton_Click イベント ハンドラーを次のように入力します。  
  
    ```c#  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     このコードは、Web ブラウザーのターゲットとしてテキスト ボックスに入力された Web アドレスを設定します。 アドレスが有効でない場合、コードはエラーをスローします。  
  
3.  WebFrame_Navigated イベントを処理する必要もあります。  
  
    ```c#  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  ソリューションをビルドします。  
  
## <a name="adding-the-user-control-to-the-start-page"></a>スタート ページにユーザー コントロールの追加  
 このコントロールを使用可能にスタート ページのプロジェクトにスタート ページのプロジェクト ファイルで、新しいコントロール ライブラリへの参照を追加します。 スタート ページの XAML マークアップに、コントロールを追加できます。  
  
1.  **ソリューション エクスプ ローラー**、スタート ページにプロジェクトを右クリックして**参照** をクリックし、**参照の追加**します。  
  
2.  **プロジェクト**] タブで [ **WebUserControl**順にクリック**OK**します。  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     ソリューションをビルド可能ユーザー コントロールの intellisense ソリューションで他のファイル。  
  
 スタート ページの XAML マークアップにコントロールを追加するには、アセンブリの名前空間の参照を追加し、ページにコントロールを配置します。  
  
#### <a name="to-add-the-control-to-the-markup"></a>コントロールのマークアップを追加するには  
  
1.  **ソリューション エクスプ ローラー**、スタート ページの .xaml ファイルを開きます。  
  
2.  **XAML**  ウィンドウで、次の名前空間宣言を最上位レベルに追加<xref:System.Windows.Controls.Grid>要素</xref:System.Windows.Controls.Grid>。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  **XAML**  ウィンドウで、スクロールして、\<グリッド >」セクション。  
  
     このセクションで説明、<xref:System.Windows.Controls.TabControl>内の要素、<xref:System.Windows.Controls.Grid>要素</xref:System.Windows.Controls.Grid></xref:System.Windows.Controls.TabControl>。  
  
4.  追加、 \<TabControl > 要素を含む、 \<TabItem > ユーザー コントロールへの参照を格納しています。  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 これで、コントロールをテストできます。  
  
## <a name="testing-a-manually-created-custom-start-page"></a>手動で作成したカスタム スタート ページのテスト  
  
1.  XAML ファイルとサポート テキスト ファイル、またはマークアップ ファイルをコピー、 **%USERPROFILE%\My documents \visual Studio 2015\StartPages\\ **フォルダーです。  
  
2.  スタート ページが、コントロールや Visual Studio がインストールされていないアセンブリ内の型を参照する場合、アセンブリをコピーし、貼り付けることで*Visual Studio インストール フォルダー***\Common7\IDE\PrivateAssemblies\\**します。  
  
3.  Visual Studio コマンド プロンプトで次のように入力します。 **devenv/rootsuffix Exp**を Visual Studio の実験用インスタンスを開きます。  
  
4.  実験用インスタンスで、**ツール/オプション/環境/スタートアップ**ページおよび元の XAML ファイルを選択、**スタート ページのカスタマイズ**ドロップダウンです。  
  
5.  **[表示]** メニューの **[スタート ページ]**をクリックします。  
  
     カスタム スタート ページが表示されます。 ファイルを変更する場合は、する必要があります実験用インスタンスを閉じる、変更を加える、コピーし変更されたファイルを貼り付けますおよび変更を表示する実験用インスタンスを再度開きます。  
  
## <a name="see-also"></a>関連項目  
 [WPF コンテナー コントロール](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [チュートリアル: カスタム XAML をスタート ページに追加します。](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
