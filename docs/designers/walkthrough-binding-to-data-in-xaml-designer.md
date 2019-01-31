---
title: XAML デザイナーでデータにバインドする
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 76ed74f6688add7892dbdbfd95a837a9bae69b96
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945308"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>チュートリアル: XAML デザイナーでデータにバインドする

XAML デザイナーでは、アートボードと [プロパティ] ウィンドウを使用してデータ バインディングのプロパティを設定できます。 このチュートリアルの例では、データをコントロールにバインドする方法を示します。 具体的には、`ItemCount` という名前の [DependencyProperty](/uwp/api/Windows.UI.Xaml.DependencyProperty) を持つ簡単なショッピング カート クラスを作成した後、`ItemCount` プロパティを [TextBlock](/uwp/api/Windows.UI.Xaml.Controls.TextBlock) コントロールの **Text** プロパティにバインドする方法を説明します。

## <a name="to-create-a-class-to-use-as-a-data-source"></a>データ ソースとして使用するクラスを作成するには

1. **[ファイル]** メニューで、**[新規]** > **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスで、**[Visual C#]** ノードまたは **[Visual Basic]** ノードを選びます。次に、**[Windows デスクトップ]** ノードを展開し、**[WPF アプリケーション]** テンプレートを選びます。

1. プロジェクトに **BindingTest** という名前を付けて、**[OK]** をクリックします。

1. **MainWindow.xaml.cs** (または **MainWindow.xaml.vb**) ファイルを開き、次のコードを追加します。 C# では、`BindingTest` 名前空間 (ファイル内の最後の閉じかっこの前) にコードを追加します。 Visual Basic の場合は、単に新しいクラスを追加します。

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   このコードでは、[PropertyMetadata](/uwp/api/Windows.UI.Xaml.PropertyMetadata) オブジェクトを使って、既定の項目数の値を 0 に設定しています。

1. **[ファイル]** メニューで、**[ビルド]**  >  **[ソリューションのビルド]** を選択します。

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>ItemCount プロパティを TextBlock コントロールにバインドするには

1. ソリューション エクスプローラーで、**MainWindow.xaml** のショートカット メニューを開き、**[デザイナーの表示]** を選びます。

1. ツールボックスで、[グリッド](/uwp/api/Windows.UI.Xaml.Controls.Grid) コントロールを選んでフォームに追加します。

1. `Grid` を選んだ状態で、[プロパティ] ウィンドウの **[DataContext]** プロパティの横にある **[新規作成]** ボタンを選びます。

1. **[オブジェクトの選択]** ダイアログ ボックスで、**[すべてのアセンブリを表示する]** チェック ボックスがオフであることを確認し、**BindingTest** 名前空間の下にある **ShoppingCart** を選んで、**[OK]** ボタンを選びます。

     次の図は、**[オブジェクトの選択]** ダイアログ ボックスで **ShoppingCart** 選んだ状態を示しています。

     ![[オブジェクトの選択] ダイアログ ボックス](../designers/media/blendselectobject.png)

1. **[ツールボックス]** で、`TextBlock` コントロールを選んでフォームに追加します。

1. `TextBlock` コントロールを選んだ状態で、[プロパティ] ウィンドウで **[Text]** プロパティの右側にあるプロパティ マーカーを選んでから、**[データ バインディングの作成]** を選びます。 (プロパティ マーカーは小さいボックスのような外観です。)

1. [データ バインディングを作成] ダイアログ ボックスの **[パス]** ボックスで、**[ItemCount: (int32)]** プロパティを選び、**[OK]** を選びます。

     次の図は、**[ItemCount]** プロパティを選んだ **[データ バインディングの作成]** ダイアログ ボックスです。

     ![[データ バインディングの作成] ダイアログ ボックス](../designers/media/xaml_create_data_binding.png)

1. **F5 キー**を押してアプリを実行します。

     `TextBlock` コントロールに、既定値の 0 がテキストとして表示されるはずです。

## <a name="see-also"></a>関連項目

- [XAML デザイナーを使用して UI を作成する](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [[値コンバーターの追加] ダイアログ ボックス](https://msdn.microsoft.com/library/c5f3d110-a541-4b55-8bca-928f77778af8)