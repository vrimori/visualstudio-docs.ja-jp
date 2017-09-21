---
title: "Visual Studio でのデータへのコントロールのバインド | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "[データ ソース] ウィンドウ"
  - "データ ソース, 表示 (データを)"
  - "データ, 表示"
  - "表示 (データを)"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio でのデータへのコントロールのバインド
データをコントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。  これらのデータ バインディング コントロールを作成するには、Visual Studio で **\[データ ソース\]** ウィンドウからデザイン サーフェイスに項目をドラッグします。  
  
 ここでは、データ バインディング コントロールを作成するために使用できるデータ ソースについて説明します。  また、データ バインディングに関連する一般的なタスクについても説明します。  データ バインディング コントロールを作成する方法の詳細については、「[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)」、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」、および「[Visual Studio でのデータへの Silverlight コントロールのバインド](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)」を参照してください。  
  
## データ ソース  
 データ ソースは、アプリケーションで使用できるデータを表します。  データ ソースは、データベース、サービス、またはオブジェクトから作成できます。  詳細については、「[データ ソースの概要](../data-tools/add-new-data-sources.md)」を参照してください。  
  
 一部のデータ ソースでは、**\[データ ソース\]** ウィンドウから項目をドラッグすることによりデータ バインディング コントロールを作成できますが、その他のデータ ソースではできません。  サポートされるデータ ソースを次の表に示します。  
  
|データ ソース|**Windows フォーム デザイナー**でのドラッグ アンド ドロップのサポート|**WPF デザイナー**でのドラッグ アンド ドロップのサポート|**Silverlight デザイナー**でのドラッグ アンド ドロップのサポート|  
|-------------|------------------------------------------------|---------------------------------------|-----------------------------------------------|  
|データセット|○|○|Ｘ|  
|エンティティ データ モデル|×<sup>1</sup>|○|○|  
|LINQ to SQL クラス|×<sup>2</sup>|×<sup>2</sup>|×<sup>2</sup>|  
|サービス \([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、WCF サービス、および Web サービスを含む\)|○|○|○|  
|オブジェクト|○|○|○|  
|SharePoint|○|○|○|  
  
 1.  Windows フォーム デザイナーが開いている場合、**\[データ ソース\]** ウィンドウ内のエンティティは読み取り専用であり、デザイナーにドラッグすることはできません。  ただし、Entity Data Model に基づく新しいオブジェクト データ ソースを追加し、それらのオブジェクトをデザイナーにドラッグすることで、データ バインディング コントロールを作成できます。  
  
 2.  LINQ to SQL クラスは、**\[データ ソース\]** ウィンドウに表示されません。  ただし、LINQ to SQL クラスに基づく新しいオブジェクト データ ソースを追加し、それらのオブジェクトをデザイナーにドラッグして、データ バインディング コントロールを作成できます。  詳細については、「[Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)」を参照してください。  
  
## データ ソース ウィンドウ  
 データ ソースは、**\[データ ソース\]** ウィンドウ内の項目としてプロジェクトで利用できます。  このウィンドウから項目をドラッグして、基になるデータにバインドされるコントロールを作成できます。  詳細については、「[ウィンドウ](../Topic/Data%20Sources%20Window.md)」を参照してください。  
  
 **\[データ ソース\]** ウィンドウに表示されるデータ型ごとに、項目をデザイナーにドラッグしたときに既定のコントロールが作成されます。  **\[データ ソース\]** ウィンドウから項目をドラッグする前に、作成されるコントロールを変更できます。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
## データへのコントロールのバインドに関連するタスク  
 コントロールをデータにバインドするために実行する最も一般的なタスクを次の表に示します。  
  
|タスク|詳細情報|  
|---------|----------|  
|**\[データ ソース\]** ウィンドウを開く。|[方法: \[データ ソース\] ウィンドウを開く](../Topic/How%20to:%20Open%20the%20data%20sources%20window.md)|  
|プロジェクトにデータ ソースを追加する。|[方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [方法: サービスのデータに接続する](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|**\[データ ソース\]** ウィンドウからデザイナーに項目をドラッグしたときに作成されるコントロールを設定する。|[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)|  
|**\[データ ソース\]** ウィンドウの項目に関連付けられるコントロールのリストを変更する。|[\[データ ソース\] ウィンドウにカスタム コントロールを追加する](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)|  
|データ バインディング コントロールを作成する。|[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [Visual Studio でのデータへの Silverlight コントロールのバインド](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 データにバインドされるコントロールを作成したら、次のタスクのいずれかを実行できます。  
  
|タスク|参照項目|  
|---------|----------|  
|基になるデータ ソースのデータを編集する。|[アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)|  
|データに加えられた変更を検証する。|[データの検証](../Topic/Validating%20Data.md)|  
|更新されたデータをデータベースに保存する。|[データの保存](../data-tools/saving-data.md)|  
  
## 参照  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Visual Studio でのデータへの Silverlight コントロールのバインド](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [方法: データベースの画像にコントロールをバインドする](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [Visual Studio でデータ ソースを操作するためのツール](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)