---
title: 複合データ バインディングをサポートする Windows フォーム ユーザー コントロールの作成 |Microsoft Docs
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de22f93c6fd04f89360fdaf8a2f5d83bd373d93d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284259"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Windows アプリケーションでフォームにデータを表示するときにから既存のコントロールを選択することができます、**ツールボックス**、またはアプリケーションが標準のコントロールで使用できない機能に必要な場合は、カスタム コントロールを作成できます。 このチュートリアルでは、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールには、データにバインドできる `DataSource` プロパティと `DataMember` プロパティが含まれます。 このようなコントロールは、<xref:System.Windows.Forms.DataGridView> や <xref:System.Windows.Forms.ListBox> に似ています。  
  
 コントロールの作成の詳細については、次を参照してください。[デザイン時に Windows フォーム コントロールの開発](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829)します。  
  
 データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性のいずれかを実装する必要があります。  
  
|データ バインディング属性の使用方法|  
|-----------------------------------|  
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 詳細については、次を参照してください。[単純データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)です。|  
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|  
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|  
  
 このチュートリアルでは、テーブルからのデータ行を表示する複合コントロールを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。 複合ユーザー コントロールは、カスタム コントロールの <xref:System.Windows.Forms.DataGridView> で Customers テーブルを表示します。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新規作成**Windows アプリケーション**します。  
  
-   新しい追加**ユーザー コントロール**をプロジェクトにします。  
  
-   ユーザー コントロールをビジュアルに設計します。  
  
-   `ComplexBindingProperty` 属性を実装します。  
  
-   使用してデータセットを作成、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。  
  
-   設定、**顧客**テーブルに、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)新しい複雑なコントロールを使用します。  
  
-   新しいコントロールをドラッグしてから、追加、**データ ソース ウィンドウ**に**Form1**します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="create-a-windows-application"></a>Windows アプリケーションを作成します。  
 作成するには、まず、 **Windows アプリケーション**します。  
  
#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには  
  
1.  Visual Studio から、**ファイル**] メニューの [新規作成**プロジェクト**します。  
  
2.  プロジェクトに名前を**ComplexControlWalkthrough**します。  
  
3.  選択**Windows アプリケーション**、 をクリック**OK**します。 詳細については、次を参照してください。[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     **ComplexControlWalkthrough**プロジェクトを作成するとに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="add-a-user-control-to-the-project"></a>ユーザー コントロールをプロジェクトに追加します。  
 このチュートリアルから複雑なデータ バインド コントロールが作成されるため、**ユーザー コントロール**、追加する必要があります、**ユーザー コントロール**をプロジェクトに項目。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加するには  
  
1.  **プロジェクト**] メニューの [選択**ユーザー コントロールの追加**します。  
  
2.  型**ComplexDataGridView**で、**名前**領域、およびクリック**追加**します。  
  
     **ComplexDataGridView**コントロールに追加されます**ソリューション エクスプ ローラー**、され、デザイナーが開きます。  
  
## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView コントロールをデザインします。  
 この手順では、ユーザー コントロールに <xref:System.Windows.Forms.DataGridView> を追加します。  
  
#### <a name="to-design-the-complexdatagridview-control"></a>ComplexDataGridView コントロールを設計するには  
  
-   ドラッグ、<xref:System.Windows.Forms.DataGridView>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。  
  
## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。  
 データ バインディングをサポートする複合コントロールには、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装できます。  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>ComplexBindingProperties 属性を実装するには  
  
1.  スイッチ、 **ComplexDataGridView**コントロールをコード ビューにします。 (上、**ビュー**メニューの **コード**)。  
  
2.  `ComplexDataGridView` のコードを次のコードで置き換えます。  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
## <a name="creating-a-data-source-from-your-database"></a>データベースからデータ ソースの作成  
 このステップでは、**データ ソースの構成**データ ソースを作成するウィザードがに基づいて、 `Customers` Northwind サンプル データベース内のテーブル。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースのセットアップについては、次を参照してください。[サンプル データベースの SQL Server のインストール](../data-tools/install-sql-server-sample-databases.md)します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソースの構成**ウィザード。  
  
3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。  
  
4.  **データ接続の選択**ページは、次のいずれか。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。  
  
5.  データベースにパスワードが必要な場合をクリックして、機密データを含めるオプションを選択**次**します。  
  
6.  **接続文字列をアプリケーション構成ファイルに保存**] ページで [**次**します。  
  
7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。  
  
8.  選択、`Customers`テーブル、およびクリックして**完了**。  
  
     **NorthwindDataSet**がプロジェクトに追加し、`Customers`テーブルに表示されます、**データ ソース**ウィンドウ。  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>ComplexDataGridView コントロールを使用して Customers テーブルを設定します。  
 内で、**データソース**ウィンドウで、フォームに項目をドラッグする前に作成するコントロールを設定することができます。  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Customers テーブルを ComplexDataGridView コントロールにバインドするように設定するには  
  
1.  開いている**Form1**デザイナー。  
  
2.  展開、**顧客**内のノード、**データソース**ウィンドウ。  
  
3.  ドロップダウン矢印をクリックして、**顧客**ノード選択**カスタマイズ**します。  
  
4.  選択、 **ComplexDataGridView**の一覧から**関連付けられたコントロール**で、**データ UI カスタマイズ オプション** ダイアログ ボックス。  
  
5.  ドロップダウン矢印をクリックして、`Customers`テーブル、および選択**ComplexDataGridView**コントロール リストから。  
  
## <a name="addcontrols-to-the-form"></a>フォームに Addcontrols  
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウから、フォームにします。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには  
  
-   メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウから、フォームにします。いることを確認、 **ComplexDataGridView**テーブルのデータを表示するコントロールを使用します。  
  
## <a name="running-the-application"></a>アプリケーションの実行  
  
#### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。 次の手順として、一般的には、次のようなことを実行します。  
  
-   他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。  
  
-   検索のシナリオをサポートするコントロールを作成します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データ ソース ウィンドウからドラッグするときに作成されるコントロールを設定します。](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows フォーム コントロール](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

