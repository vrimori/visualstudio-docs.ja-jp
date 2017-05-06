---
title: "How to: Define the Type Descriptor of a Parameter"
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
  - "Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor"
  - "BDC [SharePoint development in Visual Studio], parameter types"
  - "BDC [SharePoint development in Visual Studio], type descriptor"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], parameter types"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# How to: Define the Type Descriptor of a Parameter
  型記述子には、パラメーターのデータ型を表すプロパティが含まれています。  型記述子では、フィールド、エンティティ、またはエンティティのコレクションを定義できます。  詳細については、「[TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)」を参照してください。  
  
### パラメーターの型記述子を定義するには  
  
1.  **\[BDC メソッドの詳細\]** ウィンドウで、パラメーターの型記述子を選択します。  
  
2.  メニュー バーで、**\[表示\]**、**\[プロパティ ウィンドウ\]** の順に選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、型記述子のプロパティを設定します。  
  
     以降の手順では、型記述子をフィールド、エンティティ、またはエンティティのコレクションとして定義する方法を説明します。  
  
### フィールドを定義するには  
  
1.  **\[プロパティ\]** ウィンドウで、型記述子の **\[Name\]** プロパティを、エンティティを表す型のフィールドの名前に設定します \(FirstName など\)。  
  
2.  **\[TypeName\]** プロパティの横にある一覧で、適切なデータ型を選択します \(**\[Int32\]** など\)。  
  
     省略可能なその他のパラメーターの詳細については、「[TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)」を参照してください。  
  
### エンティティを定義するには  
  
1.  **\[プロパティ\]** ウィンドウで、**\[Name\]** プロパティを、エンティティを表す名前に設定します \(Contact など\)。  
  
2.  **\[TypeName\]** プロパティを、エンティティを表す型の完全修飾名に設定します。  この型は、プロジェクト内のクラスにすることも、ソリューションで参照されているアセンブリで定義されている型にすることも、BDC オブジェクト モデルで定義されている型にすることもできます。  
  
    -   プロジェクト内のクラスにする場合は、**\[TypeName\]** プロパティの横にある下矢印をクリックし、表示されるダイアログ ボックスで **\[現在のプロジェクト\]** タブをクリックして、プロジェクト内のクラスを選択します。  
  
         完全修飾名には、クラスの名前空間および名前と、LOB システムの名前が含まれます。  次の例では、**\[TypeName\]** プロパティの値をプロジェクト内のクラスに設定しています。  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   ソリューション内のアセンブリに配置されている型にする場合は、完全修飾名に型の名前、アセンブリの名前、バージョン番号、カルチャ、および公開キー トークンが含まれます。  
  
         次の例では、**\[TypeName\]** プロパティの値を、ソリューションで参照されているアセンブリで定義されている型に設定しています。  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   BDC オブジェクト モデルで定義されている型にする場合は、完全修飾名に型の名前空間と名前が含まれます。  
  
         次の例では、**\[TypeName\]** プロパティの値を BDC オブジェクト モデルの型に設定しています。  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  **\[BDC メソッドの詳細\]** ウィンドウで、型記述子の一覧を開き、**\[編集\]** をクリックします。  
  
     **BDC エクスプローラー**のウィンドウが表示されます。  
  
4.  **BDC エクスプローラー**で、型記述子のショートカット メニューを開き、**\[型記述子の追加\]** をクリックします。  
  
     そのエンティティ型記述子の子として新しい型記述子が追加されます。  その型記述子をフィールドとして構成します。  
  
5.  手順 4. を繰り返して、エンティティの各フィールドに対応する子の型記述子を追加します。  
  
### エンティティのコレクションを定義するには  
  
1.  **\[BDC メソッドの詳細\]** ウィンドウで、必要なパラメーターの型記述子を選択します。  
  
2.  メニュー バーで、**\[表示\]**、**\[プロパティ ウィンドウ\]** の順に選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[Name\]** プロパティを、エンティティを表す名前に設定します \(Contacts など\)。  
  
4.  **\[IsCollection\]** プロパティを \[**True**\] に設定します。  これは、この型記述子がエンティティのコレクションであることを表します。  
  
5.  **\[TypeName\]** プロパティを、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスへの参照と、エンティティを表す型の完全修飾名を含む文字列に設定します。  この型は、プロジェクト内のクラスにすることも、ソリューションで参照されているアセンブリで定義されている型にすることも、BDC オブジェクト モデルで定義されている型にすることもできます。  
  
    -   プロジェクト内のクラスにする場合は、**\[TypeName\]** プロパティの横にある下矢印をクリックし、表示されるダイアログ ボックスで **\[現在のプロジェクト\]** タブをクリックして、プロジェクト内のクラスを選択します。  
  
         完全修飾名には、クラスの名前空間および名前と、LOB システムの名前が含まれます。  
  
         次の例では、**\[TypeName\]** プロパティの値をプロジェクト内のクラスのコレクションに設定しています。  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   ソリューション内のアセンブリに配置されている型にする場合は、完全修飾名に型の名前、アセンブリの名前、バージョン番号、カルチャ、および公開キー トークンが含まれます。  
  
         次の例では、**\[TypeName\]** プロパティの値を、ソリューションで参照されているアセンブリ内の型のコレクションに設定しています。  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   BDC オブジェクト モデルで定義されている型にする場合は、完全修飾名に型の名前空間と名前のみが含まれます。  
  
         次の例では、**\[TypeName\]** プロパティの値を、BDC オブジェクト モデルで定義されている型のコレクションに設定しています。  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  **\[BDC メソッドの詳細\]** ウィンドウで、型記述子の一覧を開き、**\[編集\]** をクリックします。  
  
     **BDC エクスプローラー**のウィンドウが表示されます。  
  
7.  **BDC エクスプローラー**で、型記述子のショートカット メニューを開き、**\[型記述子の追加\]** をクリックします。  
  
     そのコレクション型記述子の子として新しい型記述子が追加されます。  その型記述子をエンティティとして構成します。  
  
## 参照  
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  