---
title: Visual Studio でのデータにコントロールをバインド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ce37768ce7a7685b89b82a04b944b7fa38af630c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio でのデータにコントロールをバインドします。
データをコントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 項目をドラッグして、これらのデータ バインド コントロールを作成することができます、**データソース**ウィンドウからデザイン サーフェイス、または Visual Studio での画面のコントロールにします。  
  
 ここでは、データ バインディング コントロールを作成するために使用できるデータ ソースについて説明します。 また、データ バインディングに関連する一般的なタスクについても説明します。 データ バインド コントロールを作成する方法の具体的な詳細については、「 [Visual Studio でデータ コントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)と[Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。  
  
## <a name="data-sources"></a>データ ソース  
 データ バインドのコンテキストでは、データ ソースは、ユーザー インターフェイスにバインドできるメモリ内のデータを表します。 実際には、データ ソースは、Entity Framework クラス、データセット、.NET プロキシ オブジェクト、LINQ to SQL クラス、または任意の .NET オブジェクトまたはコレクションにカプセル化されたサービス エンドポイントを指定できます。 一部のデータ ソースを使用すると、アイテムをドラッグしてデータ バインド コントロールを作成、**データソース**ウィンドウで、その他のデータ ソースではありません。 サポートされるデータ ソースを次の表に示します。  
  
|データ ソース|ドラッグ アンド ドロップのサポート**Windows フォーム デザイナー**|ドラッグ アンド ドロップのサポート**WPF デザイナー**|ドラッグ アンド ドロップのサポート**Silverlight デザイナー**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|データセット|[はい]|はい|×|  
|エンティティ データ モデル|[はい]<sup>1</sup>|[はい]|[はい]|  
|LINQ to SQL クラス|いいえ<sup>2</sup>|いいえ<sup>2</sup>|いいえ<sup>2</sup>|  
|サービス (含む[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、WCF services、および web サービス)|[はい]|はい|[はい]|  
|Object|[はい]|はい|[はい]|  
|SharePoint|[はい]|はい|[はい]|  
  
 1. 使用して、モデルの生成、 **Entity Data Model**ウィザード、デザイナーにそれらのオブジェクトをドラッグします。  
  
 2. LINQ to SQL クラスには表示されない、**データソース**ウィンドウです。 ただし、LINQ to SQL クラスに基づく新しいオブジェクト データ ソースを追加し、それらのオブジェクトをデザイナーにドラッグして、データ バインディング コントロールを作成できます。 詳細については、次を参照してください。[チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成する](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)です。  
  
## <a name="data-sources-window"></a>[データ ソース] ウィンドウ  
 内の項目としてデータ ソースは、プロジェクトで使用できる、**データソース**ウィンドウです。 このウィンドウが表示されている、またはからアクセス可能な**ビュー** ] メニューの [フォームのデザイン サーフェイスがプロジェクト内のアクティブなウィンドウ。 基になるデータにバインドされているコントロールを作成するには、このウィンドウから項目をドラッグすることができを右クリックして、データ ソースを構成することもできます。  
  
 ![データ ソース ウィンドウ](../data-tools/media/raddata-data-sources-window.png "raddata データ ソース ウィンドウ")  
  
 データの種類別に表示される、**データソース**ウィンドウ、デザイナーに項目をドラッグするときに既定のコントロールが作成されます。 項目をドラッグする前に、**データソース**ウィンドウで、作成されるコントロールを変更することができます。 詳細については、次を参照してください。[セットのデータ ソース ウィンドウからドラッグしたときに作成する制御](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>データへのコントロールのバインドに関連するタスク  
 次の表に、いくつかの一覧データにコントロールをバインドする最も一般的なタスクを実行します。  
  
|タスク|詳細情報|  
|----------|----------------------|  
|開く、**データソース**ウィンドウです。|デザイン画面を開き、エディター内**ビュー** > **データソース**です。|  
|データ ソースをプロジェクトに追加します。|[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)|  
|項目をドラッグしたときに作成されるコントロールの設定、**データソース**をデザイナーにウィンドウです。|[[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|内の項目に関連付けられているコントロールのリストを変更、**データソース**ウィンドウです。|[[データ ソース] ウィンドウにカスタム コントロールを追加する](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|データ バインド コントロールを作成する。|[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|  
|オブジェクトまたはコレクションにバインドします。|[Visual Studio でのオブジェクトのバインド](../data-tools/bind-objects-in-visual-studio.md)|  
|UI に表示されるデータをフィルター処理します。|[Windows フォーム アプリケーションのデータのフィルター処理および並べ替えを行う](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|コントロールのキャプションをカスタマイズします。|[Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Windows フォームでのデータ バインディング](/dotnet/framework/winforms/windows-forms-data-binding)