---
title: "エンティティ間の関連付けの作成"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 関連付け (外部コンテンツ タイプを)"
  - "BDC [Visual Studio での SharePoint 開発], 関連付け (エンティティ間の)"
  - "BDC [Visual Studio での SharePoint 開発], 作成 (関連付けを)"
  - "BDC [Visual Studio での SharePoint 開発], 関連付け (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 関連付け (外部コンテンツ タイプを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 関連付け (エンティティ間の)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 作成 (関連付けを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 関連付け (エンティティを)"
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# エンティティ間の関連付けの作成
  関連付けを作成することで、ビジネス データ接続 \(BDC\) モデルのエンティティ間の関連性を定義できます。  Visual Studio では、モデルの使用者に各関連付けに関する情報を提供するメソッドが生成されます。  これらのメソッドは、SharePoint Web パーツ、またはカスタム アプリケーションでユーザー インターフェイス \(UI\) データ リレーションシップを表示するために使用できます。  
  
## 関連付けの作成  
 Visual Studio **\[ツールボックス\]** で **\[関連付け\]** のコントロールを選択し、最初のエンティティ \(ソース エンティティと呼ばれます\) をクリックし、2 番目のエンティティを作成します \(ターゲット エンティティと呼ばれます\) をクリックすると、関連付けを。  **関連付けエディター**で関連付けの詳細を定義できます。  詳細については、「[方法: エンティティ間に関連付けを作成する](../sharepoint/how-to-create-an-association-between-entities.md)」を参照してください。  
  
## 関連付けのメソッド  
 SharePoint ビジネス データ Web パーツなどのアプリケーションは、エンティティのサービス クラスでメソッドを呼び出して関連付けを使用します。  **関連付けエディター**でメソッドを選択して、エンティティのサービス クラスにメソッドを追加できます。  
  
 既定では、**関連付けエディター**によって、ソース エンティティとターゲット エンティティに Association Navigation メソッドが追加されます。  ソース エンティティに Association Navigation メソッドを使用すると、ターゲット エンティティの一覧を取得できます。  ターゲット エンティティに Association Navigation メソッドを使用すると、ターゲット エンティティに関連するソース エンティティを取得できます。  
  
 適切な情報を返すには、これらの各メソッドにコードを追加する必要があります。  また、他の種類のメソッドを追加して、より高度なシナリオをサポートすることもできます。  これらのメソッドの詳細については、参照します [サポートされていない操作](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
## 関連付けの種類  
 BDC デザイナーでは、外部キーに基づく関連付けと外部キーなしの関連付けという 2 種類の関連付けを作成できます。  
  
### 外部キーに基づく関連付け  
 ソース エンティティの識別子と、ターゲット エンティティに定義されている型記述子を関連付けることで、外部キーに基づく関連付けを作成できます。  モデルにこの関係を使用すると、ユーザーの UI を強化できます。  たとえば、ドロップダウン リストに顧客を表示できる販売注文を作成する Outlook のフォームや、顧客のプロファイル ページを開く SharePoint の販売注文の一覧などです。  
  
 外部キーに基づく関連付けを作成するには、同じ名前と型を共有する識別子と型記述子を関連付けます。  たとえば、`Contact` エンティティと `SalesOrder` エンティティの間に外部キーに基づく関連付けを作成するとします。  `SalesOrder` エンティティは、Finder メソッドまたは SpecificFinder メソッドの戻り値パラメーターの一部として `ContactID` 型記述子を返します。  **関連付けエディター**に両方の型記述子が表示されます。  `Contact` エンティティと `SalesOrder` エンティティの間に外部キーに基づく関連付けを作成するには、これらの各フィールドの横に `ContactID` の ID を選択します。  
  
 ソース エンティティの Association Navigator メソッドに、ターゲット エンティティのコレクションを返すコードを追加します。  次の例では、ある連絡先の販売注文を返します。  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 ターゲット エンティティの Association Navigator メソッドに、ソース エンティティを返すコードを追加します。  次の例では、販売注文に関連付けられた連絡先を返します。  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### 外部キーなしの関連付け  
 フィールド型記述子に識別子をマッピングしなくても、関連付けを作成できます。  このような関連付けを作成するのは、ソース エンティティがターゲット エンティティと直接的な関係がない場合です。  たとえば、`SalesOrderDetail` テーブルには、`Contact` テーブルの主キーにマップされる外部キーがありません。  
  
 `Contact` に関連する情報を `SalesOrderDetail` テーブルに表示する場合、`Contact` エンティティと `SalesOrderDetail` エンティティの間に外部キーなしの関連付けを作成できます。  
  
 `Contact` エンティティの Association Navigation メソッドの場合、テーブルを結合するか、ストアド プロシージャを呼び出して `SalesOrderDetail` エンティティを返します。  
  
 次の例では、テーブルを結合して、すべての販売注文の詳細を返します。  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 `SalesOrderDetail` エンティティの Association Navigation メソッドの場合、関連する `Contact` を返します。  次に例を示します。  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## 参照  
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: エンティティ間に関連付けを作成する](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  