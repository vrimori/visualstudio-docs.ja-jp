---
title: WPF アプリケーションで関連するデータを表示します。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 38c25cc1631529895a11af566298ce22930a2e6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746547"
---
# <a name="display-related-data-in-wpf-applications"></a>WPF アプリケーションで関連するデータを表示します。
一部のアプリケーションでは、複数のテーブルまたは親と子の関係で相互に関連付けられているエンティティから取得したデータを使用することができます。 顧客を表示するグリッドを表示するなど、`Customers`テーブル。 別のグリッドに、関連するその顧客の注文が表示されます、ユーザーは、特定の顧客を選択するときに`Orders`テーブル。

項目をドラッグして関連するデータを表示するデータ バインド コントロールを作成することができます、**データソース**WPF デザイナーにウィンドウです。

## <a name="to-create-controls-that-display-related-records"></a>関連するレコードを表示するコントロールを作成するには

1. **データ** メニューのをクリックして**データ ソースの表示**を開くには、**データソース**ウィンドウです。

2. をクリックして**新しいデータ ソースの追加**、完了、**データ ソースの構成**ウィザード。

3. WPF デザイナーを開き、デザイナーには内の項目の有効なドロップ ターゲットのコンテナーが含まれているかどうかを確認、**データソース**ウィンドウです。

     有効なドロップ ターゲットの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。

4. **データソース**ウィンドウで、親テーブルを表すノードを展開またはリレーションシップ内のオブジェクトします。 親テーブルまたはオブジェクトは、一対多リレーションシップの「一」側です。

5. 親ノード (または親ノードに個別の項目) をドラッグしてから、**データ ソース**ウィンドウからデザイナーで有効なドロップ ターゲットにします。

     Visual Studio では、ドラッグした項目ごとに新しいデータ バインド コントロールを作成する XAML を生成します。 XAML も新しく追加<xref:System.Windows.Data.CollectionViewSource>親テーブルまたはオブジェクトのドロップ ターゲットのリソースにします。 一部のデータ ソースでは、Visual Studio には、親テーブルまたはオブジェクトにデータを読み込むコードも生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。

6. **データ ソース**ウィンドウで、関連する子テーブルまたはオブジェクトを検索します。 関連する子テーブルとオブジェクトは、データの親ノードの一覧の下部にある展開可能なノードとして表示されます。

7. 子ノード (または個別の項目の子ノード) からドラッグ、**データソース**ウィンドウからデザイナーで有効なドロップ ターゲットにします。

     Visual Studio では、ドラッグした項目のそれぞれの新しいデータ バインド コントロールを作成する XAML を生成します。 XAML も新しく追加<xref:System.Windows.Data.CollectionViewSource>子テーブルまたはオブジェクトのドロップ ターゲットのリソースにします。 この新しい<xref:System.Windows.Data.CollectionViewSource>は、親テーブルだけをデザイナーにドラッグしたオブジェクトのプロパティにバインドします。 一部のデータ ソースでは、Visual Studio には、子テーブルまたはオブジェクトにデータを読み込むコードも生成されます。

     次の図は、関連を示します**Orders**のテーブル、**顧客**にデータセット内のテーブル、**データ ソース**ウィンドウです。

     ![関係を示すデータ ソース ウィンドウ](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)