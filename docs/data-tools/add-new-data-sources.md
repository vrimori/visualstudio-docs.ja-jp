---
title: "データ ソースの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], データ ソース"
  - "データ ソース"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# データ ソースの概要
データ ソースは、アプリケーションで使用できるデータを表します。  より具体的には、データ ソースはアプリケーションで操作するデータを表します。  データ ソースは、データベース \(ローカル データベース ファイルを含む\)、サービス、およびオブジェクトから取得できます。  
  
 プロジェクトに追加したデータ ソースは、**\[データ ソース\]** ウィンドウに表示されます。  多くの場合、データ ソースを Windows フォーム デザイナー、WPF デザイナー、および Silverlight デザイナーにドラッグして、基になるデータにバインドされたコントロールを作成できます。  詳細については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。  
  
 Visual Studio には、アプリケーションでデータ ソースを作成および編集するためのツールが用意されています。  Visual Studio プロジェクトのデータ ソースは、基になるデータ ストアにより返されるオブジェクトに応じて、Entity Data Model、データセット、サービスによって返されるプロキシ オブジェクト、またはその他のオブジェクトの種類として表されます。  
  
 データ ソースの作成と編集は、**データ ソース構成ウィザード**を使用して行います。  
  
## データベースから作成されたデータ ソース  
 **データ ソース構成ウィザード** を実行し、データ ソースの種類として **\[データベース\]** を選択すると、データベースからデータ ソースを作成できます。  詳細については、「[方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)」を参照してください。  
  
 データベースからデータ ソースを作成すると、Visual Studio により*データ モデル*が生成され、プロジェクトに追加されます。  データ モデルは、データベース内の基になるデータの、厳密に型指定されたプログラミング可能なビューです。  Visual Studio を使用して、次の種類のデータ モデルを作成できます。  
  
-   [Entity Data Model](../Topic/Entity%20Data%20Model.md) に基づく概念モデル。  この種類のモデルは、Entity Framework または WCF Data Services で使用できます。  詳細については、「[エンティティ フレームワークの概要](../Topic/Entity%20Framework%20Overview.md)」および「[WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md)」を参照してください。  
  
-   型指定されたデータセット。  詳細については、「[Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)」を参照してください。  
  
-   LINQ to SQL クラス。  詳細については、「[LINQ to SQL](../Topic/LINQ%20to%20SQL.md)」を参照してください。  
  
    > [!NOTE]
    >  Entity Data Model に基づく概念モデルおよびデータセットとは異なり、LINQ to SQL クラスを**データ ソース構成ウィザード**で作成することはできません。  また、LINQ to SQL クラスは **\[データ ソース\]** ウィンドウに表示されず、したがってデザイナーにドラッグしてデータ バインド コントロールを作成することはできません。  ただし、LINQ to SQL クラスに基づくオブジェクト データ ソースを作成し、それらのオブジェクトをデザイナーにドラッグすることができます。  詳細については、「[How to: Create LINQ to SQL Classes Mapped to Tables and Views \(O\/R Designer\)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)」を参照してください。  
  
### ローカル データベース ファイルから作成されたデータ ソース  
 Access データベース \(.mdb ファイル\)、SQL Server Express LocalDB データベース \(.mdf ファイル\)、および SQL Server Express データベース \(.mdf ファイル\) の各データベース ファイルからデータ ソースを作成することもできます。  これらのデータベース ファイルからデータ ソースを作成する場合、データベース ファイルをプロジェクトに直接追加できます。  詳細については、次のトピックを参照してください。  
  
-   [ローカル データの概要](../data-tools/local-data-overview.md)  
  
-   [方法 : プロジェクトでローカル データ ファイルを管理する](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## サービスから作成されたデータ ソース  
 **データ ソース構成ウィザード**を実行し、データ ソースの種類として **\[サービス\]** を選択すると、サービスからデータ ソースを作成できます。  詳細については、「[方法: サービスのデータに接続する](../data-tools/how-to-connect-to-data-in-a-service.md)」を参照してください。  
  
 サービスからデータ ソースを作成すると、Visual Studio によりサービス参照がプロジェクトに追加されます。  また、サービスによって返されたオブジェクトに対応するプロキシ オブジェクトが作成されます。  たとえば、データセットを返すサービスは、プロジェクト内でデータセットとして表現され、特定の型を返すサービスは、プロジェクト内で、返される型として表現されます。  
  
 次の種類のサービスからデータ ソースを作成できます。  
  
-   WCF Data Services。  詳細については、「[概要](../Topic/WCF%20Data%20Services%20Overview.md)」を参照してください。  
  
-   WCF \(Windows Communication Foundation\) サービス。  詳細については、「[Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)」を参照してください。  
  
-   Web サービス  詳細については、「[Not in Build: Introduction to Programming Web Services in Managed Code](http://msdn.microsoft.com/ja-jp/bd8861f3-39e1-4c06-995e-677e007eb961)」を参照してください。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウに表示される項目は、サービスによって返されるデータに応じて異なります。  サービスによっては、**データ ソース構成ウィザード**でバインドできるオブジェクトを作成するための十分な情報を提供しないものもあります。  たとえば、サービスから型指定されていないデータセットが返される場合、ウィザードを完了しても **\[データ ソース\]** ウィンドウには項目が表示されません。  これは、型指定されていないデータセットからはスキーマが提供されず、したがってウィザードでデータ ソースを作成するための十分な情報が得られないためです。  
  
## オブジェクトから作成されたデータ ソース  
 1 つ以上のパブリック プロパティを公開する任意のオブジェクトからデータ ソースを作成できます。それには、**データ ソース構成ウィザード**を実行し、データ ソースの種類として **\[オブジェクト\]** を選択します。  オブジェクトのすべてのパブリック プロパティは、**\[データ ソース\]** ウィンドウに表示されます。  詳細については、「[方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)」を参照してください。  
  
 オブジェクトにバインドする方法の詳細については、「[Visual Studio におけるオブジェクトのバインド](../data-tools/bind-objects-in-visual-studio.md)」を参照してください。  
  
## SharePoint リストから作成されたデータ ソース  
 **データ ソース構成ウィザード**を実行し、データ ソースの種類として **\[SharePoint\]** を選択すると、SharePoint リストからデータ ソースを作成できます。  SharePoint は、[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] を介してデータを公開します。したがって SharePoint データ ソースの作成は、サービスからのデータ ソースの作成と同じです。  **データ ソース構成ウィザード**で **\[SharePoint\]** 項目をクリックすると、**\[サービス参照の追加\]** ダイアログ ボックスが表示されます。このダイアログ ボックスで、SharePoint サーバーを指定することにより SharePoint データ サービスに接続します。  詳細については、「[方法: サービスのデータに接続する](../data-tools/how-to-connect-to-data-in-a-service.md)」を参照してください。  
  
## 参照  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)