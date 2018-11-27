---
title: デバッグ中に XAML のプロパティを調べる |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30f04c3d2b2d109816ff8bcfbf17fe483f24886
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758854"
---
# <a name="inspect-xaml-properties-while-debugging"></a>デバッグ中に XAML のプロパティを調べます。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

実行中の XAML コードでのリアルタイム ビューを取得できます、 **Live Visual Tree**と**ライブ プロパティ エクスプ ローラー**します。 これらのツールは、実行中の XAML アプリケーションの UI 要素のツリー ビューを提供し、選択した UI 要素のランタイム プロパティを表示します。  
  
 これらのツールは、以下の構成で使用できます。  
  
|アプリの種類|オペレーティング システムとツール|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation (4.0 以上) のアプリケーション|Windows 7 以上|  
|Windows ストアおよび Windows Phone 8.1 のアプリ|Windows 10 以降で、 [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
|ユニバーサル Windows アプリ|Windows 10 以降で、 [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Live Visual Tree 内の要素の表示  
 リスト ビューとボタンのある非常に単純な WPF アプリケーションから開始します。 ボタンをクリックするたびに、項目が 1 つずつ一覧に追加されます。 偶数の項目は灰色で表示され、奇数の項目は黄色で表示されます。  
  
 新しい C# WPF アプリケーションを作成します ([ファイル] / [新規作成] / [プロジェクト]、その後 [C#] を選択して [WPF アプリケーション] を探します)。 名前を付けます**TestXAML**します。  
  
 MainWindow.xaml を次のように変更します。  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
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
  
 ウィンドウが表示されたら、クリックして、**項目の追加**何回かのボタンをクリックします。 次のように表示されます。  
  
 ![アプリのメイン ウィンドウ](../debugger/media/livevisualtree-app.png "LiveVIsualTree アプリ")  
  
 開き、 **Live Visual Tree**ウィンドウ (**デバッグ/Windows/Live Visual Tree**IDE の左側にあるプロパティを検索)。 このウィンドウで確認できるようにドッキング位置からドラッグし、 **Live Properties**サイド バイ サイドのウィンドウ。 **Live Visual Tree**ウィンドウで、展開、 **ContentPresenter**ノード。 これにはボタンとリスト ボックスのノードが含まれます。 リスト ボックスを展開 (をクリックし、 **ScrollContentPresenter**と**ItemsPresenter**) ボックスの項目の一覧を検索します。 ウィンドウは、次のようになります。  
  
 ![ライブ ビジュアル ツリーの ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree Listboxitem")  
  
 アプリケーション ウィンドウに戻り、さらにいくつかの項目を追加します。 表示されるリスト ボックス項目を表示する必要があります、 **Live Visual Tree**します。  
  
 次に、いずれかのリスト ボックス項目のプロパティを検討します。 内の最初のリスト ボックス項目を選択、 **Live Visual Tree**  をクリックし、**プロパティを表示**ツールバーのアイコン。 **Live Property Explorer**が表示されます。 なお、**コンテンツ**フィールドは"Item1"、および**バック グラウンド**フィールドは **#ffffffe0** (薄い黄色)。 戻り、 **Live Visual Tree** 2 番目のリスト ボックス項目を選択します。 **Live Property Explorer**を表示する必要があります、**コンテンツ**フィールドが"Item2"、および**バック グラウンド**フィールドは **#ffd3d3d3** (薄い灰色).  
  
 XAML の実際の構造にはユーザーに直接関係のない多数の要素が含まれていて、コードをよく理解していない場合は、ツリーを参照して検索対象を見つけることが困難となる可能性があります。 そのため、 **Live Visual Tree**いくつかの方法を確認する要素を検索するのに役立つアプリケーションの UI を使用することができますが。  
  
 **実行中のアプリケーションを選択できるように**します。 コントロールの左端のボタンを選択するとは、このモードを有効にすることができます、 **Live Visual Tree**ツールバー。 アプリケーションでは、UI 要素を選択するには、このモードで、 **Live Visual Tree** (および**Live Property Viewer**)、その要素に対応するツリーで、ノードの表示に自動的に更新そのプロパティを選択します。  
  
 **実行中のアプリケーションのレイアウトの装飾の表示**します。 選択を有効にするためのボタンのすぐ右にあるボタンを選択すると、このモードを有効にすることができます。 ときに**レイアウト ガイドを表示**に、アプリケーション ウィンドウに内容に合わせて配置、余白を示す四角形とを確認できるように、選択したオブジェクトの境界に沿って水平と垂直の線を表示すると、します。 たとえば、両方をオン**選択を有効にする**と**表示レイアウト**され、選択、**項目の追加**アプリケーション内のテキスト ブロック。 テキスト ブロック ノードを表示する必要があります、 **Live Visual Tree**テキスト ブロック プロパティと、 **Live Property Viewer**、テキスト ブロックの境界に水平方向および垂直の線とします。  
  
 ![Displaylayout の livepropertyviewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **選択のプレビュー**します。 このモードを有効にするには、Visual Tree ツールバーで左端から 3 番目のボタンを選択します。 このモードは、アプリケーションのソース コードにアクセスできる場合に、要素が宣言されている XAML を示します。 選択**選択を有効にする**と**選択のプレビュー**、テスト アプリケーションでは、ボタンを選択するとします。 MainWindow.xaml ファイルが Visual Studio で開き、ボタンが定義されている行にカーソルが置かれます。  
  
## <a name="using-xaml-tools-with-running-applications"></a>実行中のアプリケーションで XAML のツールを使用する  
 ソース コードがない場合でも、これらの XAML ツールを使用できます。 実行中の XAML アプリケーションにアタッチするときに使用できます、 **Live Visual Tree**そのアプリケーションの UI 要素をすぎます。 以前に使用したものと同じ WPF テスト アプリケーションを使用する例を次に示します。  
  
1.  開始、 **TestXaml**リリース構成でアプリケーション。 実行されているプロセスにアタッチすることはできません、**デバッグ**構成します。  
  
2.  Visual Studio の 2 番目のインスタンスを開き、をクリックして**デバッグ]/[プロセスにアタッチ**します。 検索**TestXaml.exe**使用可能なプロセスは、およびクリックの一覧で**アタッチ**します。  
  
3.  アプリケーションが実行を開始します。  
  
4.  Visual Studio の 2 番目のインスタンスで開く、 **Live Visual Tree** (**デバッグ/Windows/Live Visual Tree**)。 表示する必要があります、 **TestXaml** UI 要素とするようにアプリケーションを直接デバッグしたときに、それらを操作することはできます。



