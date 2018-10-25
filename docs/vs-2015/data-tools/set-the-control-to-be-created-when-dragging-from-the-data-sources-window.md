---
title: データ ソース ウィンドウからドラッグするときに作成されるコントロールの設定 |Microsoft Docs
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
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e48bac812f8d87b7e65b6a2a5832a7a36e4f95c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860358"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
項目をドラッグしてデータ バインド コントロールを作成することができます、**データソース**ウィンドウから WPF デザイナーまたは Windows フォーム デザイナーにします。 内の各項目、**データソース**ウィンドウがデザイナーにドラッグするときに作成される既定のコントロール。 ただし、別のコントロールが作成されるようにすることもできます。  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>データ テーブルまたはオブジェクトを作成するコントロールを設定します。  
 データ テーブルまたはからオブジェクトを表す項目をドラッグする前に、**データソース**ウィンドウで、1 つのコントロールにすべてのデータを表示する、または個別のコントロールの各列またはプロパティを表示するを選択できます。  
  
 このコンテキストで、用語*オブジェクト*カスタム ビジネス オブジェクト、エンティティ (Entity Data Model)、またはサービスによって返されるオブジェクトを参照します。  
  
#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>データ テーブルまたはオブジェクトに対して作成されるコントロールを設定するには  
  
1. WPF デザイナーまたは Windows フォーム デザイナーが開いていることを確認します。  
  
2. **データソース**ウィンドウで、データ テーブルを表す項目を選択するかを設定するオブジェクトします。  
  
3. 項目のドロップダウン メニューをクリックし、メニューの次の項目のいずれかをクリックします。  
  
   - 個別のコントロールに各データ フィールドを表示する**詳細**します。 データ項目をデザイナーにドラッグすると、このアクションにより、親のデータ テーブルまたはオブジェクトの列またはプロパティごとに異なるデータ バインド コントロールが作成され、各コントロールのラベルが作成されます。  
  
   - 一覧で、選択して、別のコントロールをなど 1 つのコントロールでは、すべてのデータを表示するに**DataGrid**または**一覧**WPF アプリケーション、または**DataGridView** Windows フォームでアプリケーション。  
  
     利用可能なコントロールの一覧は、デザイナーが開いている、.NET Framework のバージョン、プロジェクトのターゲットは依存し、そのサポートへのデータ バインディングを制御するかどうかを追加したカスタム、**ツールボックス**します。 作成するコントロールが利用できるコントロールのリストに含まれている場合、コントロールをリストに追加できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。  
  
     データ テーブルまたはオブジェクトのコントロールの一覧に追加できるカスタム Windows フォーム コントロールを作成する方法については、**データ ソース**ウィンドウを参照してください[複雑なデータをサポートする Windows フォーム ユーザー コントロールの作成バインド](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)します。  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>データ列またはプロパティに対して作成されるコントロールを設定します。  
 列またはからのオブジェクトのプロパティを表す項目をドラッグする前に、**データソース**をデザイナーにウィンドウを作成するコントロールを設定できます。  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>列またはプロパティに対して作成されるコントロールを設定するには  
  
1.  WPF デザイナーまたは Windows フォーム デザイナーが開いていることを確認します。  
  
2.  **データソース**ウィンドウ、またはその列またはプロパティを表示するオブジェクトを目的のテーブルを展開します。  
  
3.  作成されるコントロールを設定する各列または各プロパティを選択します。  
  
4.  列またはプロパティのドロップダウン メニューをクリックし、項目をデザイナーにドラッグしたときに作成されるコントロールを選択します。  
  
     利用可能なコントロールの一覧は、デザイナーが開いている、.NET Framework のバージョン、プロジェクトのターゲットは依存し、どのカスタム コントロールに追加したデータ バインディングをサポートする、**ツールボックス**します。 作成するコントロールが利用できるコントロールのリストに含まれている場合、コントロールをリストに追加できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。  
  
     コントロールのデータ列またはプロパティの一覧に追加できるカスタム コントロールを作成する方法について、**データソース**ウィンドウを参照してください[の単純データバインディングをサポートするWindowsフォームユーザーコントロールを作成します](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。  
  
     列またはプロパティのコントロールを作成しない場合は、選択**None**ドロップダウン メニュー。 これは、親のテーブルまたはオブジェクトをデザイナーにドラッグする必要があり、かつ特定の列またはプロパティを含める必要がない場合に便利です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)

