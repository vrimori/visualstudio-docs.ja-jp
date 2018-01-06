---
title: "デバッグ中に XAML のプロパティを検査 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 70ca76a3b611b0490def98b1a24936f71ca42e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inspect-xaml-properties-while-debugging"></a>デバッグ中に XAML のプロパティを調べます。
実行中の XAML コードのリアルタイム ビューを取得することができます、 **Live Visual Tree**と**Live Property Explorer**です。 これらのツールは、実行中の XAML アプリケーションの UI 要素のツリー ビューを提供し、選択した UI 要素のランタイム プロパティを表示します。  
  
 これらのツールは、以下の構成で使用できます。  
  
|アプリの種類|オペレーティング システムとツール|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation (4.0 以上) のアプリケーション|Windows 7 以上|  
|Windows 8.1 と Windows Phone 8.1 アプリ|Windows 10 以上で、 [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
|ユニバーサル Windows アプリ|Windows 10 以上で、 [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Live Visual Tree 内の要素の表示  
 リスト ビューとボタンのある非常に単純な WPF アプリケーションを開始しましょう。 ボタンをクリックするたびに、項目が 1 つずつ一覧に追加されます。 偶数の項目は灰色で表示され、奇数の項目は黄色で表示されます。  
  
 新しい c# WPF アプリケーションの作成 (ファイル > 新規 > プロジェクトを選択 (C#) し、WPF アプリケーションの検索)。 名前を付けます**TestXAML**です。  
  
 MainWindow.xaml を次のように変更します。  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 以下のコマンド ハンドラーを MainWindow.xaml.cs ファイルに追加します。  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 プロジェクトをビルドし、デバッグを開始します。 (ビルド構成はリリースではなくデバッグでなければなりません。 ビルド構成の詳細については、次を参照してください[ビルド構成について](../ide/understanding-build-configurations.md)。)。  
  
 ウィンドウが表示されたら、クリックして、**項目の追加**2 ~ 3 回ボタンをクリックします。 次のように表示されます。  
  
 ![アプリのメイン ウィンドウ](../debugger/media/livevisualtree-app.png "LiveVIsualTree アプリ")  
  
 開くように、 **Live Visual Tree**ウィンドウ (**デバッグ > Windows > Live Visual Tree**、または IDE の左側で探します)。 このウィンドウを検索できるようにドッキング位置からドラッグし、 **Live Properties**サイド バイ サイドのウィンドウ。 **Live Visual Tree**ウィンドウで、展開、 **ContentPresenter**ノード。 これにはボタンとリスト ボックスのノードが含まれます。 リスト ボックスを展開 (し、 **ScrollContentPresenter**と**ItemsPresenter**)、リスト ボックス項目を検索します。 ウィンドウは、次のようになります。  
  
 ![ライブ ビジュアル ツリー内の Listboxitem](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree Listboxitem")  
  
 アプリケーション ウィンドウに戻り、さらにいくつかの項目を追加します。 表示される複数のリスト ボックス項目が表示されます、 **Live Visual Tree**です。  
  
 これで、リスト ボックス項目のいずれかのプロパティを見てみましょう。 内の最初のリスト ボックス項目を選択して、 **Live Visual Tree**  をクリックし、**プロパティを表示**ツールバーのアイコン。 **Live Property Explorer**が表示されます。 なお、**コンテンツ**フィールドは"Item1"、および**バック グラウンド**フィールドは**#ffffffe0** (薄い黄色)。 戻り、 **Live Visual Tree** 2 番目のリスト ボックス項目を選択します。 **Live Property Explorer**を表示する必要があります、**コンテンツ**フィールドが"Item2"、および**背景**フィールドは**#ffd3d3d3** (薄い灰色).  
  
 XAML の実際の構造は多数の関心がある可能性があります直接、要素を持ち、コードをよく理解していない場合は、探しているものを検索するツリーを移動するハード時を必要があります。 そのため、 **Live Visual Tree**いくつかの方法を確認する場合の要素を検索するため、アプリケーションの UI を使用することができますがします。  
  
 **実行中のアプリケーションを選択できるように**です。 左端のボタンを選択するときに、このモードを有効にすることができます、 **Live Visual Tree**ツールバー。 このモードでは、アプリケーションでは、UI 要素を選択できますと**Live Visual Tree** (および**Live Property Viewer**) 自動的に更新されて、その要素に対応するツリー内のノードの表示そのプロパティを選択します。  
  
 **実行中のアプリケーションでレイアウトの装飾を表示**です。 選択を有効にするためのボタンのすぐ右にあるボタンを選択すると、このモードを有効にすることができます。 ときに**レイアウトの装飾を表示**が有効になって、アプリケーション ウィンドウ内容に合わせて配置、および、余白を示す四角形を表示できるように選択したオブジェクトの境界に沿って水平および垂直方向の線の表示になります。 たとえば、両方をオン**を選択できるように**と**表示レイアウト**され、選択、**項目の追加**アプリケーション内のテキスト ブロックします。 テキスト ブロック ノードを表示する必要があります、 **Live Visual Tree** 、テキスト ブロック プロパティと、 **Live Property Viewer**、テキスト ブロックの境界に水平と垂直の線とします。  
  
 ![DisplayLayout で LivePropertyViewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **選択のプレビュー**です。 このモードを有効にするには、Visual Tree ツールバーで左端から 3 番目のボタンを選択します。 このモードは、アプリケーションのソース コードにアクセスできる場合に、要素が宣言されている XAML を示します。 選択**を選択できるように**と**選択のプレビュー**、テスト アプリケーションで、ボタンを選択します。 MainWindow.xaml ファイルが Visual Studio で開き、ボタンが定義されている行にカーソルが置かれます。  
  
## <a name="using-xaml-tools-with-running-applications"></a>実行中のアプリケーションで XAML のツールを使用する  
 ソース コードがあるない場合でも、これらの XAML ツールを使用することができます。 実行中の XAML アプリケーションにアタッチする際に使用できます、 **Live Visual Tree**そのアプリケーションの UI 要素をすぎます。 を以前に使用した同じ WPF テスト アプリケーションを使用する例を次に示します。  
  
1.  開始、 **TestXaml**リリース構成でアプリケーションです。 実行されているプロセスにアタッチすることはできません、**デバッグ**構成します。  
  
2.  Visual Studio の 2 番目のインスタンスを開き、をクリックして**デバッグ > プロセスにアタッチする**です。 検索**TestXaml.exe**選択可能なプロセスとクリックの一覧で**アタッチ**です。  
  
3.  アプリケーションが実行を開始します。  
  
4.  Visual Studio の 2 番目のインスタンスで開く、 **Live Visual Tree** (**デバッグ > Windows > Live Visual Tree**)。 表示されるはずの**TestXaml** UI 要素とすることができるよう、アプリケーションを直接デバッグしたときにそれらの操作です。