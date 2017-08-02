---
title: "方法: WPF アプリケーションで関連データを表示する | Microsoft Docs"
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法: WPF アプリケーションで関連データを表示する
アプリケーションによっては、親子のリレーションシップによって相互に関連付けられた複数のテーブルやエンティティから取得したデータを使用する場合があります。  たとえば、`Customers` テーブルの顧客を表示するグリッドを表示するような場合です。  ユーザーが特定の顧客を選択すると、関連する `Orders` テーブルを使用して、その顧客の注文が別のグリッドに表示されます。  
  
 **\[データ ソース\]** ウィンドウから WPF デザイナーに項目をドラッグすると、関連データを表示するデータ バインド コントロールを作成できます。  
  
### 関連するレコードを表示するコントロールを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックして **\[データ ソース\]** ウィンドウを開きます。  
  
2.  **\[新しいデータ ソースの追加\]** をクリックして、**データ ソース構成**ウィザードの操作を完了します。  
  
3.  WPF デザイナーを開き、**\[データ ソース\]** ウィンドウ内の項目に対して有効なドロップ ターゲットとなるコンテナーが、WPF デザイナーに含まれていることを確認します。  
  
     有効なドロップ ターゲットの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
4.  **\[データ ソース\]** ウィンドウで、リレーションシップの親テーブルまたは親オブジェクトを表すノードを展開します。  親テーブルまたは親オブジェクトは、一対多リレーションシップの "一" の側のテーブルまたはオブジェクトです。  
  
5.  **\[データ ソース\]** ウィンドウから、親ノード \(または親ノード内の個別の項目\) をデザイナー内の有効なドロップ ターゲットにドラッグします。  
  
     ドラッグした各項目に対して新しいデータ バインド コントロールを作成する XAML が、Visual Studio によって生成されます。  さらに、この XAML により、親テーブルまたは親オブジェクトの新しい <xref:System.Windows.Data.CollectionViewSource> がドロップ ターゲットのリソースに追加されます。  一部のデータ ソースでは、Visual Studio により、親テーブルまたは親オブジェクトにデータを読み込むためのコードも生成されます。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
6.  **\[データ ソース\]** ウィンドウで、関連する子テーブルまたは子オブジェクトを見つけます。  データの親ノードの一覧の下部に、関連する子テーブルと子オブジェクトが展開可能なノードとして表示されます。  
  
7.  **\[データ ソース\]** ウィンドウから、子ノード \(または子ノードの個別の項目\) をデザイナー内の有効なドロップ ターゲットにドラッグします。  
  
     ドラッグした各項目に対して新しいデータ バインド コントロールを作成する XAML が、Visual Studio によって生成されます。  さらに、この XAML により、子テーブルまたは子オブジェクトの新しい <xref:System.Windows.Data.CollectionViewSource> がドロップ ターゲットのリソースに追加されます。  この新しい <xref:System.Windows.Data.CollectionViewSource> が、デザイナーにドラッグした親テーブルまたは親オブジェクトのプロパティにバインドされます。  一部のデータ ソースでは、Visual Studio により、子テーブルまたは子オブジェクトにデータを読み込むためのコードも生成されます。  
  
     次の図は、**\[データ ソース\]** ウィンドウのデータセットに表示された、**Customers** テーブルに関連する **Orders** テーブルを示しています。  
  
     ![関係を示すデータ ソース ウィンドウ](~/data-tools/media/datasources2.gif "DataSources2")  
  
## 参照  
 [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [方法: Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [方法: WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)