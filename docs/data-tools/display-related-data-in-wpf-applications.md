---
title: WPF アプリケーションで関連データを表示する
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 2fe1a41792aa6712f61b2d034cac75528108a722
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940896"
---
# <a name="display-related-data-in-wpf-applications"></a>WPF アプリケーションで関連データを表示する

一部のアプリケーションでは、複数のテーブルまたは親と子のリレーションシップで相互に関連するエンティティから取得したデータを操作する可能性があります。 顧客を表示するグリッドを表示するなど、`Customers`テーブル。 別のグリッドがから、関連する顧客の注文を表示、ユーザーは、特定の顧客を選択するときに`Orders`テーブル。

項目をドラッグして関連データを表示するデータ バインド コントロールを作成することができます、**データソース**WPF デザイナーにウィンドウ。

## <a name="to-create-controls-that-display-related-records"></a>関連するレコードを表示するコントロールを作成するには

1. **[データ]** メニューの **[データ ソースの表示]** をクリックして **[データ ソース]** ウィンドウを開きます。

2. **[新しいデータ ソースの追加]** をクリックして、**データ ソース構成ウィザード**の操作を完了します。

3. WPF デザイナーを開き、デザイナーには内の項目の有効なドロップ先であるコンテナーが含まれているかどうかを確認して、**データソース**ウィンドウ。

     有効なドロップ ターゲットの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)します。

4. **データソース**ウィンドウ、またはリレーションシップのオブジェクトを親テーブルを表すノードを展開します。 親テーブルまたはオブジェクトは、一対多リレーションシップの「一」側では。

5. 親ノード (または親ノードでの個別の項目) をドラッグしてから、**データ ソース**ウィンドウからデザイナーで有効なドロップ ターゲットにします。

     Visual Studio には、各アイテムをドラッグするための新しいデータ バインド コントロールを作成する XAML が生成されます。 XAML も新しく追加<xref:System.Windows.Data.CollectionViewSource>親テーブルまたはドロップ先のリソースへのオブジェクト。 一部のデータ ソースでは、Visual Studio には、親テーブルまたはオブジェクトに、データを読み込むコードも生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)します。

6. **データソース**ウィンドウで、関連する子テーブルまたはオブジェクトを検索します。 関連する子テーブルとオブジェクトは、データの親ノードの一覧の下部にある展開可能なノードとして表示されます。

7. 子ノード (または個別の項目の子ノード) をドラッグしてから、**データ ソース**デザイナーで有効なドロップ ターゲット上にウィンドウ。

     Visual Studio には、ドラッグした項目のそれぞれの新しいデータ バインド コントロールを作成する XAML が生成されます。 XAML も新しく追加<xref:System.Windows.Data.CollectionViewSource>子テーブルまたはドロップ先のリソースへのオブジェクト。 この新しい<xref:System.Windows.Data.CollectionViewSource>親テーブルをデザイナーにドラッグしたオブジェクトのプロパティにバインドされます。 一部のデータ ソースでは、Visual Studio には、子テーブルまたはオブジェクトに、データを読み込むコードも生成されます。

     次の図は、関連する**注文**のテーブル、**顧客**にデータセット内のテーブル、**データソース**ウィンドウ。

     ![関係を示すデータ ソース ウィンドウ](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)