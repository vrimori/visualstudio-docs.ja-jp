---
title: "方法: WPF アプリケーションでルックアップ テーブルを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "データ [WPF], 表示"
  - "データ バインド, WPF"
  - "表示 (データを), WPF"
  - "WPF [WPF], データ"
  - "WPF データ バインド [Visual Studio]"
  - "WPF デザイナー, データ バインド"
  - "WPF, データ バインド (Visual Studio での)"
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法: WPF アプリケーションでルックアップ テーブルを作成する
**\[データ ソース\]** ウィンドウ内の親テーブルまたは親オブジェクトのメイン ノードを、関連する子テーブルの列またはプロパティにバインドされたコントロールにドラッグすると、ルックアップ テーブルを作成できます。  *ルックアップ テーブル* \(*検索バインド*と呼ばれることもあります\) とは、あるテーブルの外部キー フィールドの値に基づいて別のデータ テーブルの情報を表示するコントロールを表します。  
  
 たとえば、販売データベースの `Orders` テーブルであれば、次のように使用されます。  `Orders` テーブルの各レコードには、注文した顧客を表す `CustomerID` が含まれます。  `CustomerID` は、`Customers` テーブルの顧客レコードを指す外部キーです。  `Orders` テーブルの注文の一覧を表示する場合に、`CustomerID` ではなく、実際の顧客名を表示できます。  顧客名は `Customers` テーブルに格納されているため、顧客名を表示するにはルックアップ テーブルを作成する必要があります。  ルックアップ テーブルでは、`Orders` レコードの `CustomerID` の値を使用してリレーションシップをたどり、わかりやすい顧客名を返します。  
  
### ルックアップ テーブルを作成するには  
  
1.  プロジェクトに、関連データを持つ次のいずれかの種類のデータ ソースを追加します。  
  
    -   データセットまたは Entity Data Model。  詳細については、「[方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)」を参照してください。  
  
    -   WCF データ サービス、WCF サービス、または Web サービス。  詳細については、「[方法: サービスのデータに接続する](../data-tools/how-to-connect-to-data-in-a-service.md)」を参照してください。  
  
    -   オブジェクト。  詳細については、「[方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)」を参照してください。  
  
    > [!NOTE]
    >  ルックアップ テーブルを作成するには、関連する 2 つのテーブルまたはオブジェクトがプロジェクトのデータ ソースとして存在している必要があります。  
  
2.  **WPF デザイナー**を開き、**\[データ ソース\]** ウィンドウ内の項目に対して有効なドロップ ターゲットとなるコンテナーが、WPF デザイナーに含まれていることを確認します。  
  
     有効なドロップ ターゲットの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
3.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックして **\[データ ソース\]** ウィンドウを開きます。  
  
4.  **\[データ ソース\]** ウィンドウで、親テーブルまたは親オブジェクトと関連する子テーブルまたは子オブジェクトが表示されるまでノードを展開します。  
  
    > [!NOTE]
    >  関連する子テーブルまたは子オブジェクトは、親テーブルまたは親オブジェクトの下に展開可能な子ノードとして表示されるノードです。  
  
5.  子ノードのドロップダウン メニューをクリックし、**\[詳細\]** を選択します。  
  
6.  子ノードを展開します。  
  
7.  子ノードの下で、子と親のデータを関連付けている項目のドロップダウン メニューをクリックします \(上の例の場合、これは **\[CustomerID\]** ノードになります\)。  検索バインドをサポートする次のいずれかの種類のコントロールを選択します。  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  **ListBox** コントロールまたは **ListView** コントロールが一覧に表示されない場合は、これらのコントロールを一覧に追加できます。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
    -   <xref:System.Windows.Controls.Primitives.Selector> から派生した任意のカスタム コントロール。  
  
        > [!NOTE]
        >  **\[データ ソース\]** ウィンドウの項目に対して選択できるコントロールの一覧にカスタム コントロールを追加する方法については、「[\[データ ソース\] ウィンドウにカスタム コントロールを追加する](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)」を参照してください。  
  
8.  **\[データ ソース\]** ウィンドウから、WPF デザイナー内のコンテナーに子ノードをドラッグします \(上の例の場合、子ノードは **\[Orders\]** ノードです\)。  
  
     ドラッグした各項目に対して新しいデータ バインド コントロールを作成する XAML が、Visual Studio によって生成されます。  さらに、この XAML により、子テーブルまたは子オブジェクトの新しい <xref:System.Windows.Data.CollectionViewSource> がドロップ ターゲットのリソースに追加されます。  一部のデータ ソースでは、Visual Studio により、テーブルまたはオブジェクトにデータを読み込むコードも生成されます。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
9. **\[データ ソース\]** ウィンドウから、前の手順で作成した検索バインド コントロールに親ノードをドラッグします \(上の例の場合、親ノードは **\[Customers\]** ノードです\)。  
  
     Visual Studio は、コントロールのいくつかのプロパティを設定して検索バインドを構成します。  Visual Studio によって変更されるプロパティを次の表に示します。  必要に応じて、これらのプロパティを XAML または **\[プロパティ\]** ウィンドウで変更できます。  
  
    |プロパティ|設定の説明|  
    |-----------|-----------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|このプロパティは、コントロールに表示するデータの取得に使用するコレクションまたはバインドを指定します。  このプロパティは、Visual Studio によって、コントロールにドラッグした親データの <xref:System.Windows.Data.CollectionViewSource> に設定されます。|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|このプロパティは、コントロールに表示するデータ項目のパスを指定します。  このプロパティは、Visual Studio によって、親データ内で主キーの後にあり、文字列データ型を含んでいる最初の列またはプロパティに設定されます。<br /><br /> 親データの別の列またはプロパティを表示する場合は、このプロパティを別のプロパティのパスに変更します。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|このプロパティは、Visual Studio によって、デザイナーにドラッグした子データの列またはプロパティにバインドされます。  この列またはプロパティが、親データの外部キーになります。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|このプロパティは、Visual Studio によって、親データの外部キーである子データの列またはプロパティのパスに設定されます。|  
  
## 参照  
 [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [方法: Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [方法: WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)   
 [チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)