---
title: "Visual Studio でのデータへの Windows フォーム コントロールのバインド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Windows フォーム], データ ソース"
  - "データ [Windows フォーム], 表示"
  - "データ ソース, 表示 (データを)"
  - "表示 (データをフォームに)"
  - "表示 (データを), Windows フォーム"
  - "フォーム, 表示 (データを)"
  - "Windows フォーム, データ バインド"
  - "Windows フォーム, 表示 (データを)"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio でのデータへの Windows フォーム コントロールのバインド
データを Windows フォームにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。  これらのデータ バインド コントロールを作成するには、Visual Studio で **\[データ ソース\]** ウィンドウから Windows フォーム デザイナーに項目をドラッグします。  このトピックでは、データ バインド Windows フォーム アプリケーションの作成に使用できる最も一般的なタスク、ツール、およびクラスについて説明します。  
  
 Visual Studio でのデータ バインド コントロールの作成方法に関する一般的な情報については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。  Windows フォームでのデータ バインディングの詳細については、「[Windows フォームでのデータ バインド](../Topic/Windows%20Forms%20Data%20Binding.md)」を参照してください。  
  
## Windows アプリケーションのフォーム上のデータ表示に必要なタスク  
 Windows アプリケーションのフォーム上のデータ表示に関連する一般的なタスクを次の表に示します。  
  
|タスク|詳細情報|  
|---------|----------|  
|データ バインド コントロールを作成する。<br /><br /> 既存のコントロールをデータにバインドする。|[方法: Windows フォーム コントロールをデータにバインドする](../data-tools/bind-windows-forms-controls-to-data.md)|  
|親子のリレーションシップの関連データを表示するコントロールを作成する \(あるコントロールでデータ レコードを選択すると、選択したレコードに関連するデータが別のコントロールに表示される\)。|[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)|  
|*ルックアップ テーブル*を作成する。  ルックアップ テーブルには、あるテーブルの情報が、別のテーブルの外部キー フィールドの値に基づいて表示されます。|[方法: Windows フォーム アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|表示データの制御方法を書式設定する。|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/ja-jp/42638120-9e6f-436b-985f-4036664230fd)|  
|**\[データ ソース\]** ウィンドウのスマート キャプション機能の動作を変更する。|[方法 : Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|パラメーター クエリを実行するコントロールを追加する。|[方法: パラメーター クエリを Windows フォーム アプリケーションに追加する](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|イメージ コントロールを使用してデータベース内のイメージを表示するように列を設定する。|[方法: データベースの画像にコントロールをバインドする](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|データセット内のデータのフィルター処理または並べ替えを行う。|[方法: Windows フォーム アプリケーションのデータのフィルター処理および並べ替えを行う](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 次のトピックでは、Windows フォーム コントロールをデータにバインドする例を示します。  
  
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 データベースのデータを照会する方法、およびそのデータを Windows フォームに表示する方法の詳細な手順について説明します。  
  
 [チュートリアル: Windows フォームでの関連データの表示](../Topic/Walkthrough:%20Displaying%20Related%20Data%20on%20a%20Windows%20Form.md)  
 2 つの関連するテーブルからデータを表示する方法、およびそのデータを Windows フォームに表示する方法の詳細な手順について説明します。  
  
 [チュートリアル: データを検索する Windows フォームの作成](../data-tools/create-a-windows-form-to-search-data.md)  
 ユーザー入力に基づいてデータベース検索を実行する Windows フォームを作成する方法の詳細な手順について説明します。  
  
 [チュートリアル: Windows フォーム アプリケーションでのルックアップ テーブルの作成](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 別のテーブルで選択されたデータに基づくテーブルのデータを表示する方法の詳細な手順について説明します。  
  
 [チュートリアル: Windows フォーム間でのデータの受け渡し](../data-tools/pass-data-between-forms.md)  
 アプリケーション内のあるフォームから別のフォームへ値を受け渡す方法の詳細な手順について説明します。  
  
 [チュートリアル: 単純データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 **\[データ ソース\]** ウィンドウで使用できるカスタム コントロールを作成する方法の詳細な手順について説明します。  
  
 [チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 **\[データ ソース\]** ウィンドウで使用できるカスタム コントロールを作成する方法の詳細な手順について説明します。  
  
 [チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 **\[データ ソース\]** ウィンドウで使用できるカスタム コントロールを作成する方法の詳細な手順について説明します。  
  
## データ スマート タグ  
 データ操作用のスマート タグは、多くのコントロールで利用できます。  フォームにいくつかのコントロールを追加すると、データに関連する一連の操作をスマート タグで使用できるようになります。  
  
## BindingSource コンポーネント  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは 2 つの目的で利用できます。  まず、フォームのコントロールをデータにバインドするときに、抽象化レイヤーの役割を果たします。  フォーム上のコントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントにバインドされます \(データ ソースに直接バインドされるわけではありません\)。  
  
 また、オブジェクトのコレクションを管理できます。  <xref:System.Windows.Forms.BindingSource> に型を追加すると、その型の一覧が作成されます。  
  
 <xref:System.Windows.Forms.BindingSource> コンポーネントの詳細については、次のトピックを参照してください。  
  
-   [BindingSource コンポーネント](../Topic/BindingSource%20Component.md)  
  
-   [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [BindingSource コンポーネント アーキテクチャ](../Topic/BindingSource%20Component%20Architecture.md)  
  
## BindingNavigator コントロール  
 このコンポーネントには、Windows アプリケーションによって表示されるデータを移動するためのユーザー インターフェイスが用意されています。  詳細については、「[BindingNavigator コントロール](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md)」を参照してください。  
  
## DataGridView コントロール  
 <xref:System.Windows.Forms.DataGridView> コントロールを使用すると、さまざまな種類のデータ ソースのデータを表形式で表示したり編集したりできます。  <xref:System.Windows.Forms.DataGridView> にデータをバインドするには、<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを使用します。  詳細については、「[DataGridView コントロールの概要](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [チュートリアル: 単純データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)