---
title: データ コントロールをバインドします。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ff7c2db3fc1032e08a9e15f17ca6ae1af6d9373b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991633"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio でのデータへのコントロールのバインド

データをコントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 項目をドラッグして、これらのデータ バインド コントロールを作成することができます、**データソース**をデザイン画面または Visual Studio での画面のコントロールにウィンドウ。

ここでは、データ バインディング コントロールを作成するために使用できるデータ ソースについて説明します。 また、データ バインディングに関連する一般的なタスクについても説明します。 データ バインド コントロールを作成する方法の詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)と[Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)します。

## <a name="data-sources"></a>データ ソース

データ バインディングのコンテキストでは、データ ソースは、ユーザー インターフェイスにバインドできるメモリ内のデータを表します。 実際には、データ ソースは、Entity Framework のクラス、データセット、.NET プロキシ オブジェクト、LINQ to SQL クラス、または任意の .NET オブジェクトまたはコレクションでカプセル化されたサービス エンドポイントをすることができます。 一部のデータ ソースでは、**[データ ソース]** ウィンドウから項目をドラッグすることによりデータ バインディング コントロールを作成できますが、その他のデータ ソースではできません。 サポートされるデータ ソースを次の表に示します。

| データ ソース | **Windows フォーム デザイナー**でのドラッグ アンド ドロップのサポート | **WPF デザイナー**でのドラッグ アンド ドロップのサポート | **Silverlight デザイナー**でのドラッグ アンド ドロップのサポート |
| - | - | - | - |
| データセット | はい | はい | × |
| エンティティ データ モデル | ○<sup>1</sup> | はい | はい |
| LINQ to SQL クラス | ×<sup>2</sup> | ×<sup>2</sup> | ×<sup>2</sup> |
| サービス ([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、WCF サービス、および Web サービスを含む) | はい | はい | はい |
| Object | はい | はい | はい |
| SharePoint | はい | はい | はい |

1. 使用して、モデルの生成、 **Entity Data Model**ウィザード、デザイナーにそれらのオブジェクトをドラッグします。

2. LINQ to SQL クラスは、**[データ ソース]** ウィンドウに表示されません。 ただし、LINQ to SQL クラスに基づく新しいオブジェクト データ ソースを追加し、それらのオブジェクトをデザイナーにドラッグして、データ バインディング コントロールを作成できます。 詳細については、「[チュートリアル:LINQ to SQL クラス (O/R デザイナー) を作成する](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)します。

## <a name="data-sources-window"></a>[データ ソース] ウィンドウ

データ ソースは、**[データ ソース]** ウィンドウ内の項目としてプロジェクトで利用できます。 フォームのデザイン サーフェイスは、プロジェクトのアクティブ ウィンドウまたは選択して開く (ときに、プロジェクトを開く) ことができる場合、このウィンドウが表示される**ビュー** > **その他の Windows**  >  **データ ソース**します。 基になるデータにバインドされているコントロールを作成するには、このウィンドウから項目をドラッグすることができを右クリックし、データ ソースを構成することもできます。

![[データ ソース] ウィンドウ](../data-tools/media/raddata-data-sources-window.png)

**[データ ソース]** ウィンドウに表示されるデータ型ごとに、項目をデザイナーにドラッグしたときに既定のコントロールが作成されます。 項目をドラッグする前に、**データソース**ウィンドウで、作成されるコントロールを変更することができます。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

## <a name="tasks-involved-in-binding-controls-to-data"></a>データへのコントロールのバインドに関連するタスク

次の表に、いくつかの一覧にコントロールをデータにバインドする最も一般的なタスクを実行します。

|タスク|詳細情報|
|----------| - |
|**[データ ソース]** ウィンドウを開く。|デザイン画面を開き、エディター内**ビュー** > **データソース**します。|
|プロジェクトにデータ ソースを追加する。|[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)|
|**[データ ソース]** ウィンドウからデザイナーに項目をドラッグしたときに作成されるコントロールを設定する。|[[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|**[データ ソース]** ウィンドウの項目に関連付けられるコントロールのリストを変更する。|[[データ ソース] ウィンドウにカスタム コントロールを追加する](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|データ バインド コントロールを作成する。|[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|オブジェクトまたはコレクションにバインドします。|[Visual Studio でのオブジェクトのバインド](../data-tools/bind-objects-in-visual-studio.md)|
|UI に表示されるデータをフィルター処理します。|[Windows フォーム アプリケーションのデータのフィルター処理および並べ替えを行う](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|コントロールのキャプションをカスタマイズします。|[Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows フォームでのデータ バインディング](/dotnet/framework/winforms/windows-forms-data-binding)
