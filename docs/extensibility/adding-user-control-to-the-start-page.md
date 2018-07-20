---
title: スタート ページにユーザー コントロールの追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 095325fc8312747b61ff4312c5fe616ae79ce045
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152959"
---
# <a name="add-user-control-to-the-start-page"></a>スタート ページにユーザー コントロールを追加します。
このチュートリアルでは、カスタム スタート ページへの DLL の参照を追加する方法を示します。 例では、ソリューションにユーザー コントロールを追加、ユーザー コントロールをビルドおよびスタート ページからビルドされたアセンブリを参照 *.xaml*ファイル。 新しいタブでは、基本的な Web ブラウザーとして機能するユーザー コントロールをホストします。  
  
 呼び出すことができる任意のアセンブリを追加するのと同じプロセスを使用することができます、 *.xaml*ファイル。  
  
## <a name="add-a-wpf-user-control-to-the-solution"></a>ソリューションに WPF ユーザー コントロールを追加します。  
 最初に、スタート ページのソリューションに Windows Presentation Foundation (WPF) ユーザー コントロールを追加します。  
  
1.  [作成を使用して開始] ページで作成した[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)します。  
  
2.  **ソリューション エクスプ ローラー**は、ソリューションを右クリックし、[**追加**、] をクリックし、**新しいプロジェクト**します。  
  
3.  左側のウィンドウで、**新しいプロジェクト** ダイアログ ボックスで、いずれかを展開、 **Visual Basic**または**Visual c#** ノード、およびクリック**Windows**。 中央のペインで選択**WPF ユーザー コントロール ライブラリ**します。  
  
4.  コントロールに名前を`WebUserControl` をクリックし、 **OK**します。  
  
## <a name="implement-the-user-control"></a>ユーザー コントロールを実装します。  
 WPF ユーザー コントロールを実装するには、XAML でユーザー インターフェイス (UI) を構築し、c# または他の .NET 言語で分離コードのイベントを書き込みます。  
  
### <a name="to-write-the-xaml-for-the-user-control"></a>ユーザー コントロールの XAML を記述するには  
  
1.  ユーザー コントロールの XAML ファイルを開きます。 `<Grid>`要素、コントロールに次の行の定義を追加します。  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  メイン`<Grid>`要素、次の新しい追加`<Grid>`要素で、Web アドレスと、新しいアドレスを設定するためのボタン入力用のテキスト ボックスが含まれています。  
  
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
  
3.  次のフレームを最上位レベルに追加`<Grid>`要素直後、 `<Grid>` button と textbox を含む要素。  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  次の例では、ユーザー コントロールの完成した XAML を示します。  
  
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
  
### <a name="to-write-the-code-behind-events-for-the-user-control"></a>ユーザー コントロールの分離コードのイベントの書き込み  
  
1.  XAML デザイナーで、ダブルクリック、**アドレスの設定**コントロールに追加したボタンをクリックします。  
  
     *UserControl1.cs*コード エディターでファイルが開きます。  
  
2.  SetButton_Click イベント ハンドラーで、次のように入力します。  
  
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
  
     このコードは、Web ブラウザーのターゲットとして、テキスト ボックスに型指定された Web アドレスを設定します。 アドレスが有効でない場合、コードはエラーをスローします。  
  
3.  WebFrame_Navigated イベントを処理することも必要があります。  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  ソリューションをビルドします。  
  
## <a name="add-the-user-control-to-the-start-page"></a>スタート ページに、ユーザー コントロールを追加します。  
 このコントロールで使用できるように、スタート ページ プロジェクトにスタート ページ プロジェクト ファイルでは、新しいコントロール ライブラリへの参照を追加します。 スタート ページの XAML マークアップをコントロールを追加できます。  
  
1.  **ソリューション エクスプ ローラー**、スタート ページ プロジェクトを右クリックして**参照**順にクリックします**参照の追加**します。  
  
2.  **プロジェクト**] タブで [ **WebUserControl**順にクリックします**OK**します。  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
     ソリューションを構築可能ユーザー コントロールに IntelliSense ソリューションで他のファイル。  
  
 スタート ページの XAML マークアップには、コントロールを追加するには、アセンブリへの参照を名前空間を追加し、ページにコントロールを配置します。  
  
### <a name="to-add-the-control-to-the-markup"></a>コントロールのマークアップを追加するには  
  
1.  **ソリューション エクスプ ローラー**、スタート ページを開く *.xaml*ファイル。  
  
2.  **XAML**ウィンドウで、最上位レベルに次の名前空間宣言を追加<xref:System.Windows.Controls.Grid>要素。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  **XAML**ウィンドウまでスクロールすると、\<グリッド > セクション。  
  
     セクションが含まれて、<xref:System.Windows.Controls.TabControl>内の要素を<xref:System.Windows.Controls.Grid>要素。  
  
4.  追加、 \<TabControl > 要素を含む、 \<TabItem > ユーザー コントロールへの参照を格納しています。  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 これで、コントロールをテストできます。  
  
## <a name="test-a-manually-created-custom-start-page"></a>手動で作成したカスタム スタート ページをテストします。  
  
1.  コピーは、XAML ファイルとサポート テキスト ファイルまたはマークアップをファイルに、 *%USERPROFILE%\My documents \visual Studio 2015 \startpages\\* フォルダー。  
  
2.  スタート ページは、すべてのコントロールまたは Visual Studio がインストールされていないアセンブリで型を参照する場合、アセンブリをコピーし、貼り付けることで * Visual Studio インストール フォルダー ***\Common7\IDE\PrivateAssemblies\\** .  
  
3.  Visual Studio コマンド プロンプトで「 **devenv/rootsuffix Exp**を Visual Studio の実験用インスタンスを開きます。  
  
4.  実験用のインスタンスに移動、**ツール** > **オプション** > **環境** > **スタートアップ**ページおよび元の XAML ファイルを選択、**スタート ページのカスタマイズ**ドロップダウンします。  
  
5.  **[表示]** メニューの **[スタート ページ]** をクリックします。  
  
     カスタム スタート ページが表示されます。 ファイルを変更する場合は、する必要があります実験用インスタンスを閉じて、変更を行います、コピーし、変更されたファイルを貼り付けるして変更を表示する実験用インスタンスを再度開きます。  
  
## <a name="see-also"></a>関連項目  
 [コンテナーの WPF コントロール](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [チュートリアル: カスタム XAML をスタート ページに追加します。](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)