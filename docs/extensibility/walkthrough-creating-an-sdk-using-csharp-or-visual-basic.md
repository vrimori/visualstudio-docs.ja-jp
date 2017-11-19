---
title: "チュートリアル: c# または Visual Basic を使用して、SDK の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5f944dad46225a70192bbfb0dbd0d1dc6dc861a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>チュートリアル: c# または Visual Basic を使用して、SDK の作成
このチュートリアルでは、Visual c# を使用して単純な数値演算ライブラリ SDK を作成し、SDK と Visual Studio Extension (VSIX) パッケージ化する方法を学習します。 次の手順を完了します。  
  
-   [SimpleMath Windows ランタイム コンポーネントを作成するには](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [SimpleMathVSIX 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [クラス ライブラリを使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
##  <a name="createClassLibrary"></a>SimpleMath Windows ランタイム コンポーネントを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**新しいプロジェクト**です。  
  
2.  テンプレートの一覧で展開**Visual c#**または**Visual Basic**、選択、 **Windows ストア** ノードを選択し、 **のWindowsランタイムコンポーネント**テンプレート。  
  
3.  **名前**ボックスで、指定**SimpleMath**を選択し、 **OK**ボタンをクリックします。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMath**プロジェクト ノードをクリックして**プロパティ**です。  
  
5.  名前を変更**Class1.cs**に**Arithmetic.cs**し、次のコードに一致するように更新します。  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**ソリューション 'SimpleMath'**  ノードを選択し**Configuration Manager**です。  
  
     **Configuration Manager**  ダイアログ ボックスが表示されます。  
  
7.  **アクティブ ソリューション構成**一覧で、選択**リリース**です。  
  
8.  **構成**列、いることを確認**SimpleMath**に設定されている行**リリース**を選択し、**閉じる**ボタンをクリックして、変更します。  
  
    > [!IMPORTANT]
    >  SimpleMath コンポーネント用の SDK には、1 つだけ構成が含まれています。 この構成は、リリース ビルドである必要がありますまたはコンポーネントを使用するアプリの証明を渡さない、[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]です。  
  
9. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMath**プロジェクト ノードをクリックして**ビルド**です。  
  
##  <a name="createVSIX"></a>SimpleMathVSIX 拡張機能プロジェクトを作成するには  
  
1.  ショートカット メニューで、**ソリューション 'SimpleMath'**  ノードを選択して**追加**、**新しいプロジェクト**です。  
  
2.  テンプレートの一覧で展開**Visual c#**または**Visual Basic**、選択、**機能拡張** ノードを選択し、 **VSIX プロジェクト**テンプレートです。  
  
3.  **名前**ボックスで、指定**SimpleMathVSIX**を選択し、 **OK**ボタンをクリックします。  
  
4.  **ソリューション エクスプ ローラー**、選択、 **source.extension.vsixmanifest**項目。  
  
5.  メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
6.  既存の XML を次の XML に置き換えます。  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  **ソリューション エクスプ ローラー**、選択、 **SimpleMathVSIX**プロジェクト。  
  
8.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
9. 一覧で**共通項目**、展開**データ**を選択し**XML ファイル**です。  
  
10. **名前**ボックスで、指定`SDKManifest.xml`を選択し、**追加**ボタンをクリックします。  
  
11. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 `SDKManifest.xml`、選択**プロパティ**、しの値を変更し、 **VSIX に含める**プロパティを**True**です。  
  
12. ファイルの内容を次の XML に置き換えます。  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMathVSIX**プロジェクト**追加**を選択し**新しいフォルダー**です。  
  
14. フォルダーの名前を`references`です。  
  
15. ショートカット メニューを開き、**参照**フォルダーを選択して**追加**を選択し**新しいフォルダー**です。  
  
16. サブフォルダーの名前を変更`commonconfiguration`、内のサブフォルダーを作成し、サブフォルダーの名前、`neutral`です。  
  
17. この時間に最初のフォルダーの名前を変更する前の 4 つの手順を繰り返して`redist`です。  
  
     プロジェクトには、次のフォルダー構造が含まれています。  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMath**プロジェクトをクリックして**ファイル エクスプ ローラーでフォルダーを開く**です。  
  
19. **ファイル エクスプ ローラー**bin \release フォルダーに移動し、SimpleMath.winmd ファイルのショートカット メニューを開きを選択し**コピー**です。  
  
20. **ソリューション エクスプ ローラー**、references\commonconfiguration\neutral のフォルダーにファイルを貼り付け、 **SimpleMathVSIX**プロジェクト。  
  
21. SimpleMath.pri ファイル redist\commonconfiguration\neutral のフォルダーに貼り付けることにより、前の手順を繰り返して、 **SimpleMathVSIX**プロジェクト。  
  
22. **ソリューション エクスプ ローラー**、選択**SimpleMath.winmd**です。  
  
23. メニュー バーで、次のように選択します。**ビュー**、**プロパティ**(キーボード: F4 キーを押します)。  
  
24. **プロパティ**ウィンドウで、変更、**ビルド アクション**プロパティを**コンテンツ**、し、変更、 **VSIX に含める**プロパティ**True**です。  
  
25. **ソリューション エクスプ ローラー**、このプロセスを繰り返します**SimpleMath.pri**です。  
  
26. **ソリューション エクスプ ローラー**、選択、 **SimpleMathVSIX**プロジェクト。  
  
27. メニュー バーで、次のように選択します。**ビルド**、**ビルド SimpleMathVSIX**です。  
  
28. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMathVSIX**プロジェクトをクリックして**ファイル エクスプ ローラーでフォルダーを開く**です。  
  
29. **ファイル エクスプ ローラー**\bin\Release フォルダーに移動、およびインストールする SimpleMathVSIX.vsix を実行します。  
  
30. 選択、**インストール**ボタンをクリックし、インストールが終了するまで待機し、Visual Studio を再起動します。  
  
##  <a name="createSample"></a>クラス ライブラリを使用するサンプル アプリを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**新しいプロジェクト**です。  
  
2.  テンプレートの一覧で展開**Visual c#**または**Visual Basic**を選択し、 **Windows ストア**ノード。  
  
3.  選択、**空のアプリケーション**名では、プロジェクト テンプレートは、 **ArithmeticUI**を選択し、 **OK**ボタンをクリックします。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ArithmeticUI**プロジェクトをクリックして**追加**、**参照**です。  
  
5.  参照型の一覧で展開**Windows**を選択し**拡張**です。  
  
6.  詳細ウィンドウで、選択、**単純な数値演算 SDK**拡張機能です。  
  
     SDK に関する追加情報が表示されます。 できます、**詳細**このチュートリアルで先ほど SDKManifest.xml ファイルで指定したとおり、http://www.msdn.microsoft.com を開くためのリンク。  
  
7.  **参照マネージャー**ダイアログ ボックスで、**単純な数値演算 SDK**チェック ボックスをオンにして、 **OK**ボタンをクリックします。  
  
8.  メニュー バーで、次のように選択します。**ビュー**、**オブジェクト ブラウザー**です。  
  
9. **参照**一覧で、選択**単純な計算**です。  
  
     今すぐ、SDK にはどのようなを調べることができます。  
  
10. **ソリューション エクスプ ローラー**MainPage.xaml を開き、その内容を次の XAML に置き換えます。  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. MainPage.xaml.cs を次のコードを更新します。  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. アプリの実行に F5 キーを押します。  
  
13. アプリで、任意の 2 つの数値を入力してください。、、の操作を選択し、、  **=** ボタンをクリックします。  
  
     正しい結果が表示されます。  
  
 正常に作成し、拡張機能 SDK を使用します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: C++ を使用して SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [チュートリアル: JavaScript を使用して SDK を作成します。](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [ソフトウェア開発キットを作成する](../extensibility/creating-a-software-development-kit.md)