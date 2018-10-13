---
title: Visual Studio でのデータへのコントロールのバインド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a4143777e51a03867e94f1d4ebdd9c8182a5401
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291573"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio でのデータ コントロールをバインドします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
データをコントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 項目をドラッグして、これらのデータ バインド コントロールを作成することができます、**データソース**をデザイン画面または Visual Studio での画面のコントロールにウィンドウ。  
  
 ここでは、データ バインディング コントロールを作成するために使用できるデータ ソースについて説明します。 また、データ バインディングに関連する一般的なタスクについても説明します。 データ バインド コントロールを作成する方法の詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)と[Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
## <a name="data-sources"></a>データ ソース  
 データ バインディングのコンテキストでは、データ ソースは、ユーザー インターフェイスにバインドできるメモリ内のデータを表します。 実際には、データ ソースは、Entity Framework のクラス、データセット、.NET プロキシ オブジェクト、LINQ to SQL クラス、または任意の .NET オブジェクトまたはコレクションでカプセル化されたサービス エンドポイントをすることができます。 一部のデータ ソースから項目をドラッグしてデータ バインド コントロールを作成することを有効にする、**データソース**ウィンドウで、他のデータ ソースがないです。 サポートされるデータ ソースを次の表に示します。  
  
|データ ソース|ドラッグ アンド ドロップのサポート**Windows フォーム デザイナー**|ドラッグ アンド ドロップのサポート**WPF デザイナー**|ドラッグ アンド ドロップのサポート**Silverlight デザイナー**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|データセット|はい|[はい]|いいえ|  
|エンティティ データ モデル|[はい]<sup>1</sup>|はい|はい|  
|LINQ to SQL クラス|×<sup>2</sup>|×<sup>2</sup>|×<sup>2</sup>|  
|サービス (を含む[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]、WCF サービス、および web サービス)|はい|[はい]|はい|  
|Object|はい|[はい]|はい|  
|SharePoint|はい|[はい]|はい|  
  
 1. 使用して、モデルの生成、 **Entity Data Model**ウィザード、デザイナーにそれらのオブジェクトをドラッグします。  
  
 2. LINQ to SQL クラスに表示されない、**データソース**ウィンドウ。 ただし、LINQ to SQL クラスに基づく新しいオブジェクト データ ソースを追加し、それらのオブジェクトをデザイナーにドラッグして、データ バインディング コントロールを作成できます。 詳細については、次を参照してください。[チュートリアル: LINQ to SQL クラス (O/r デザイナー) を作成する](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)します。  
  
## <a name="data-sources-window"></a>[データ ソース] ウィンドウ  
 内の項目としてデータ ソースがプロジェクトで使用できる、**データソース**ウィンドウ。 このウィンドウが表示される、またはからにアクセスできる、**ビュー**メニューで、フォームのデザイン サーフェイスは、プロジェクト内のアクティブなウィンドウ。 基になるデータにバインドされているコントロールを作成するには、このウィンドウから項目をドラッグすることができを右クリックし、データ ソースを構成することもできます。  
  
 ![データ ソース ウィンドウ](../data-tools/media/raddata-data-sources-window.png "raddata データ ソース ウィンドウ")  
  
 表示されるデータ型ごとに、**データソース**ウィンドウで、デザイナーに項目をドラッグするときに既定のコントロールが作成されました。 項目をドラッグする前に、**データソース**ウィンドウで、作成されるコントロールを変更することができます。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>データをコントロールのバインドに関連するタスク  
 次の表に、いくつかの一覧にコントロールをデータにバインドする最も一般的なタスクを実行します。  
  
|タスク|詳細情報|  
|----------|----------------------|  
|開く、**データソース**ウィンドウ。|デザイン画面を開き、エディター内**ビュー** > **データソース**します。|  
|データ ソースをプロジェクトに追加します。|[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)|  
|項目をドラッグしたときに作成されるコントロールの設定、**データソース**をデザイナーにウィンドウ。|[[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|内の項目に関連付けられているコントロールのリストを変更して、**データソース**ウィンドウ。|[[データ ソース] ウィンドウにカスタム コントロールを追加する](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|データ バインド コントロールを作成する。|[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|  
|オブジェクトまたはコレクションにバインドします。|[Visual Studio でのオブジェクトのバインド](../data-tools/bind-objects-in-visual-studio.md)|  
|UI に表示されるデータをフィルター処理します。|[Windows フォーム アプリケーションのデータのフィルター処理および並べ替えを行う](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|コントロールのキャプションをカスタマイズします。|[Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Windows フォームでのデータ バインディング](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)

