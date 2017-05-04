---
title: "方法: Finder メソッドにフィルター記述子を追加する | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 追加 (フィルターを)"
  - "BDC [Visual Studio での SharePoint 開発], フィルター記述子"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 追加 (フィルターを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], フィルター記述子"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: Finder メソッドにフィルター記述子を追加する
  フィルター記述子を使用すると、モデルのコンシューマーが、メソッドを実行する前にメソッドに値を渡せるようになります。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
 たとえば、SharePoint のユーザーが、特定の条件に一致する外部コンテンツ タイプのインスタンスを取得できるようにするには、  Finder メソッドにフィルター記述子を追加します。  
  
### Finder メソッドにフィルター記述子を追加するには  
  
1.  **\[BDC メソッドの詳細\]** ウィンドウで、Finder メソッドのノードを展開し、**\[パラメーター\]** ノードを展開して、入力パラメーターを追加します。  詳細については、「[方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)」を参照してください。  
  
2.  **\[メソッドの詳細\]** ウィンドウで、パラメーターの型記述子を選択します。  
  
3.  メニュー バーで、**\[表示\]**、**\[プロパティ ウィンドウ\]** の順に選択します。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[型の名前\]** プロパティを、フィルターに対応するデータ型に設定します。  
  
     たとえば、メソッドから返される販売注文の数を注文日で制限する  フィルターをサポートするには、型記述子の **\[型の名前\]** プロパティを「**System.DateTime**」に設定する必要があります。  
  
5.  **\[メソッドの詳細\]** ウィンドウで、**\[フィルター記述子\]** ノードを展開します。  
  
6.  **\[フィルター記述子の追加\]** の一覧で、**\[フィルター記述子の作成\]** をクリックします。  
  
     **\[フィルター記述子\]** ノードの下に新しいフィルター記述子が表示されます。  
  
7.  メニュー バーで、**\[表示\]**、**\[プロパティ ウィンドウ\]** の順に選択します。  
  
8.  **\[プロパティ\]** ウィンドウで、**\[種類\]** のプロパティをクリックします。  
  
9. **\[種類\]** のプロパティに表示されるリストでは、目的のフィルター パターンを選択します。  
  
     たとえば、販売注文の数を注文日で制限するのを使用するフィルターを作成するには、Finder メソッドで、**\[比較\]** をクリックします返されました。  比較フィルターは、Finder メソッドは、特定の条件を満たすインスタンスが保証されます。  各フィルター パターンに関する詳細については、参照します [BDC でサポートされているフィルターの種類](http://go.microsoft.com/fwlink/?LinkId=169287)。  
  
10. **\[プロパティ\]** ウィンドウで、**\[関連付けられた型記述子\]** のプロパティをクリックします。  
  
11. **\[関連付けられた型記述子\]** のプロパティに表示される一覧で、先ほど作成した型記述子を選択します。  これにより、このフィルターが Finder メソッドの入力パラメーターに関連付けられます。  
  
12. データを返す Finder メソッドにコードを追加します。  入力パラメーターを SELECT クエリの条件として使用できます。  
  
     次の例では、指定した注文日の販売注文を返します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## 参照  
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  