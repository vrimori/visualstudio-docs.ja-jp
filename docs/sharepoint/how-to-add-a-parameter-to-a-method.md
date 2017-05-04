---
title: "方法 : メソッドにパラメーターを追加する | Microsoft Docs"
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
  - "BDC [Visual Studio での SharePoint 開発], 追加 (パラメーターにメソッドを)"
  - "BDC [Visual Studio での SharePoint 開発], メソッド パラメーター"
  - "BDC [Visual Studio での SharePoint 開発], パラメーター"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 追加 (パラメーターにメソッドを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], メソッド パラメーター"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], パラメーター"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法 : メソッドにパラメーターを追加する
  パラメーターを使用して、メソッドと情報をやり取りします。  すべてのメソッドには最低パラメーターが 1 つ必要です。  作成するメソッドの種類をサポートするパラメーターを設計する方法の詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
 パラメーターをメソッドを追加すると、プロジェクトのモデル ファイルの XML に、`<Parameter>` 要素が追加されます。  `<Parameter>` の要素の属性の詳細については、参照します [パラメーター](http://go.microsoft.com/fwlink/?LinkId=169284)。  
  
### メソッドにパラメーターを追加するには  
  
1.  エンティティにメソッドを追加します。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     **\[BDC メソッドの詳細\]** ウィンドウが表示されます。  詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
3.  **\[BDC メソッドの詳細\]** ウィンドウで、メソッドのノードを展開し、**\[パラメーター\]** ノードを展開します。  
  
4.  **\[パラメーターの追加\]** の一覧で、**\[パラメーターの作成\]** をクリックします。  
  
     **\[パラメーター\]** ノードの下に新しいパラメーターが表示されます。  
  
5.  メニュー バーで、**\[表示\]**、**\[プロパティ ウィンドウ\]** の順に選択します。  
  
6.  **プロパティ** ウィンドウで、**"名前"** プロパティをわかりやすい名前に設定します。  たとえば、メソッドが顧客を返す場合、GetCustomers というメソッド名が考えられます。  
  
7.  **\[BDC メソッドの詳細\]** ウィンドウで、パラメーターの方向に表示される開き、**\[InOut\]**、**\[出力\]**、または **\[戻り値\]\[入力\]** をクリックしますリストを返します。  
  
     作成する種類のメソッドに関して選択する方向の詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
8.  パラメーターの型記述子を変更します。  詳細については、「[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)」を参照してください。  
  
## 参照  
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  