---
title: "スタート ページにユーザー コントロールを追加する |Microsoft ドキュメント"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ed511fa58ca0d98d38ed2ab1ed3bc24bed642170
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="adding-user-control-to-the-start-page"></a>スタート ページにユーザー コントロールを追加します。
このチュートリアルでは、カスタム スタート ページへの参照を DLL を追加する方法を示します。 例では、ソリューションにユーザー コントロールがユーザー コントロールをビルドし、スタート ページの .xaml ファイルからビルドされたアセンブリを参照を追加します。 新しいタブでは、基本的な Web ブラウザーとして機能する、ユーザー コントロールをホストします。  
  
 同じプロセスを使用して、.xaml ファイルから呼び出すことができる任意のアセンブリを追加することができます。  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>ソリューションへの WPF ユーザー コントロールの追加  
 最初に、スタート ページのソリューションに Windows Presentation Foundation (WPF) のユーザー コントロールを追加します。  
  
1.  スタート ページを作成するで作成したを使用して[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)です。  
  
2.  **ソリューション エクスプ ローラー**ソリューションを右クリックしをクリックして**追加**、クリックして**新しいプロジェクト**です。  
  
3.  左側のウィンドウで、**新しいプロジェクト** ダイアログ ボックスで、いずれかを展開、 **Visual Basic**または**Visual c#**ノード、およびクリック**Windows**です。 中央のペインで選択**WPF ユーザー コントロール ライブラリ**です。  
  
4.  コントロールの名前を付けます`WebUserControl` をクリックし、 **OK**です。  
  
## <a name="implementing-the-user-control"></a>ユーザー コントロールを実装します。  
 WPF ユーザー コントロールを実装するのに XAML でのユーザー インターフェイス (UI) を構築し、c# または他の .NET 言語で分離コードのイベントを書き込みます。  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>ユーザー コントロールの XAML を記述するには  
  
1.  ユーザー コントロールの XAML ファイルを開きます。 \<グリッド > 要素をコントロールに、次の行の定義を追加します。  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  メイン`Grid`要素、新規の次の追加`Grid`要素は、Web アドレスと、新しいアドレスを設定するためのボタンを入力するテキスト ボックスが含まれています。  
  
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
  
3.  次のフレームを最上位レベルに追加`Grid`要素直後、 `Grid` button と textbox を格納する要素。  
  
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
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>ユーザー コントロールのコード ビハインド イベントの書き込み  
  
1.  XAML デザイナーで、ダブルクリック、**アドレスの設定**ボタン コントロールに追加します。  
  
     UserControl1.cs ファイルは、コード エディターで開きます。  
  
2.  SetButton_Click イベント ハンドラーを次のように入力します。  
  
    ```csharp  
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
  
     このコードは、Web ブラウザーのターゲットとして、テキスト ボックスに入力する Web アドレスを設定します。 アドレスが有効でない場合、コードはエラーをスローします。  
  
3.  また、WebFrame_Navigated イベントを処理する必要があります。  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  ソリューションをビルドします。  
  
## <a name="adding-the-user-control-to-the-start-page"></a>スタート ページにユーザー コントロールの追加  
 このコントロールで利用可能にスタート ページ プロジェクトにスタート ページ プロジェクト ファイルで、新しいコントロール ライブラリへの参照を追加します。 スタート ページの XAML マークアップにコントロールを追加できます。  
  
1.  **ソリューション エクスプ ローラー**、スタート ページ プロジェクトを右クリックして**参照** をクリックし、**参照の追加**です。  
  
2.  **プロジェクト** タブで  **WebUserControl**  をクリックし、 **ok**です。  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     ソリューションを構築可能ユーザー コントロールに IntelliSense ソリューションで他のファイル。  
  
 スタート ページの XAML マークアップにコントロールを追加するには、名前空間の参照をアセンブリを追加し、ページにコントロールを配置します。  
  
#### <a name="to-add-the-control-to-the-markup"></a>コントロールのマークアップを追加するには  
  
1.  **ソリューション エクスプ ローラー**、スタート ページの .xaml ファイルを開きます。  
  
2.  **XAML**  ウィンドウで、最上位レベルに次の名前空間宣言を追加<xref:System.Windows.Controls.Grid>要素。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  **XAML**  ウィンドウで、スクロール、\<グリッド > セクションでします。  
  
     セクションが含まれて、<xref:System.Windows.Controls.TabControl>内の要素、<xref:System.Windows.Controls.Grid>要素。  
  
4.  追加、 \<TabControl > 要素を含む、 \<TabItem > ユーザー コントロールへの参照を格納しています。  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 これで、コントロールをテストできます。  
  
## <a name="testing-a-manually-created-custom-start-page"></a>手動で作成したカスタム スタート ページのテスト  
  
1.  XAML ファイル、および、サポート テキスト ファイルやマークアップ ファイルにコピー、 **%USERPROFILE%\My documents \visual Studio 2015 \startpages\\ **フォルダーです。  
  
2.  スタート ページが、コントロールや Visual Studio がインストールされていないアセンブリ内の型を参照する場合、アセンブリをコピーしでそれらを貼り付け*Visual Studio インストール フォルダー***\Common7\IDE\PrivateAssemblies\\**です。  
  
3.  Visual Studio コマンド プロンプトで「 **devenv/rootsuffix Exp**を Visual Studio の実験用インスタンスを開きます。  
  
4.  実験用インスタンスに移動、**ツール/オプション/環境/スタートアップ**ページの XAML ファイルをクリックし、**スタート ページのカスタマイズ**ドロップダウンします。  
  
5.  **[表示]** メニューの **[スタート ページ]**をクリックします。  
  
     カスタム スタート ページが表示されます。 ファイルを変更する場合は、する必要がありますの実験用インスタンスを閉じて、変更、コピー貼り付け、変更されたファイルを開き直します実験用インスタンスの変更を表示します。  
  
## <a name="see-also"></a>関連項目  
 [コンテナーの WPF コントロール](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [チュートリアル: カスタム XAML をスタート ページに追加する](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
