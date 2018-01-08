---
title: "データ ソース ウィンドウからドラッグしたときに作成するコントロールを設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5556a5d9a537684a8d1e73ee363b4c9ac8f6baa8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する
項目をドラッグしてデータ バインド コントロールを作成することができます、**データソース**ウィンドウから WPF デザイナーまたは Windows フォーム デザイナーにします。 内の各項目、**データソース**ウィンドウがデザイナーにドラッグするときに作成される既定のコントロールです。 ただし、別のコントロールが作成されるようにすることもできます。  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>データ テーブルまたはオブジェクトを作成するコントロールを設定します。  
データ テーブルまたはからオブジェクトを表す項目をドラッグする前に、**データソース**ウィンドウで、1 つのコントロールのすべてのデータを表示するか、別のコントロールに各列またはプロパティを表示するを選択できます。  
  
このコンテキストで用語*オブジェクト*カスタム ビジネス オブジェクト、エンティティ (Entity Data Model)、またはサービスによって返されたオブジェクトを参照します。  
  
### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>データ テーブルまたはオブジェクトに対して作成されるコントロールを設定するには  
  
1.  WPF デザイナーまたは Windows フォーム デザイナーが開いていることを確認します。  
  
2.  **データソース**ウィンドウで、データ テーブルを表す項目を選択するかを設定するオブジェクトします。  
  
3.  項目のドロップダウン メニューをクリックし、メニューの次の項目のいずれかをクリックします。  
  
    -   個別のコントロールの各データ フィールドを表示するクリックして**詳細**です。 データ項目をデザイナーにドラッグすると、このアクションにより、親のデータ テーブルまたはオブジェクトの列またはプロパティごとに異なるデータ バインド コントロールが作成され、各コントロールのラベルが作成されます。  
  
    -   1 つのコントロールでのすべてのデータを表示するなどの選択、別のコントロール一覧で、 **DataGrid**または**リスト**WPF アプリケーションでまたは**DataGridView** Windows フォームでアプリケーション。  
  
    使用可能なコントロールのリストは、デザイナーを開いている、.NET Framework のバージョン、プロジェクトのターゲットは依存しており、そのサポートへのデータ バインディングを制御するかどうかを追加したカスタム、**ツールボックス**です。 作成するコントロールが利用できるコントロールの一覧にない場合は、一覧に、コントロールを追加できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)です。  
  
    データ テーブルまたはオブジェクト内のコントロールの一覧に追加できるカスタム Windows フォーム コントロールを作成する方法について、**データソース**ウィンドウを参照してください[複雑なデータをサポートする Windows フォーム ユーザー コントロールを作成します。バインド](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)です。  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>データ列またはプロパティに対して作成されるコントロールを設定します。  
列またはからのオブジェクトのプロパティを表す項目をドラッグする前に、**データソース**をデザイナーにウィンドウを作成するコントロールを設定できます。  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>列またはプロパティに対して作成されるコントロールを設定するには  
  
1.  WPF デザイナーまたは Windows フォーム デザイナーが開いていることを確認します。  
  
2.  **データソース** ウィンドウで、目的のテーブルを展開またはオブジェクトをその列またはプロパティを表示します。  
  
3.  作成されるコントロールを設定する各列または各プロパティを選択します。  
  
4.  列またはプロパティのドロップダウン メニューをクリックし、項目をデザイナーにドラッグしたときに作成されるコントロールを選択します。  
  
     使用可能なコントロールのリストは、デザイナーを開いている、.NET Framework のバージョン、プロジェクトのターゲットは依存しており、カスタム コントロールを追加したデータ バインディングをサポートする、**ツールボックス**です。 作成するコントロールが利用できるコントロールのリストに含まれている場合、コントロールをリストに追加できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)です。  
  
     コントロールのデータ列またはプロパティの一覧に追加できるカスタム コントロールを作成する方法について、**データソース**ウィンドウを参照してください[の単純データバインディングをサポートするWindowsフォームユーザーコントロールを作成します。](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     列またはプロパティのコントロールを作成しない場合は、選択**None**ドロップダウン メニューにします。 これは、親のテーブルまたはオブジェクトをデザイナーにドラッグする必要があり、かつ特定の列またはプロパティを含める必要がない場合に便利です。  
  
## <a name="see-also"></a>関連項目
[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)