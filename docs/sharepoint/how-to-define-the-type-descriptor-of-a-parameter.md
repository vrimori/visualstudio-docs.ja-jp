---
title: "方法: パラメーターの型記述子を定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19722a4cffb0e3708939734253b0f2c4a408389e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>方法: パラメーターの型記述子を定義する
  型記述子には、パラメーターのデータ型を表すプロパティが含まれています。 型記述子では、フィールド、エンティティ、またはエンティティのコレクションを定義できます。 詳細については、次を参照してください。 [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)です。  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>パラメーターの型記述子を定義するには  
  
1.  **BDC メソッドの詳細**ウィンドウで、パラメーターの型記述子を選択します。  
  
2.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。  
  
3.  **プロパティ**ウィンドウで、型記述子のプロパティを設定します。  
  
     以降の手順では、型記述子をフィールド、エンティティ、またはエンティティのコレクションとして定義する方法を説明します。  
  
### <a name="to-define-a-field"></a>フィールドを定義するには  
  
1.  **プロパティ**ウィンドウで、設定、**名前**エンティティを表す型のフィールドの名前に、型記述子のプロパティ (例: **FirstName**)。  
  
2.  横にある一覧で、 **TypeName**プロパティ、適切なデータ型を選択して (たとえば、 **Int32**)。  
  
     その他の省略可能なパラメーターについては、次を参照してください。 [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)です。  
  
### <a name="to-define-an-entity"></a>エンティティを定義するには  
  
1.  **プロパティ**ウィンドウで、設定、**名前**プロパティ、エンティティを説明する名前を (例:**連絡先**)。  
  
2.  設定、 **TypeName**プロパティをエンティティを表す型の完全修飾名。 この型は、プロジェクト内のクラスにすることも、ソリューションで参照されているアセンブリで定義されている型にすることも、BDC オブジェクト モデルで定義されている型にすることもできます。  
  
    -   プロジェクトのクラスは、下矢印を選択 の横に、 **TypeName**プロパティを選択、**現在のプロジェクト** タブで、プロジェクトのクラスを選択し、表示されるダイアログ ボックス。  
  
         完全修飾名には、クラスの名前空間および名前と、LOB システムの名前が含まれます。 次の例の値の設定、 **TypeName**プロパティをプロジェクト内のクラスです。  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   ソリューション内のアセンブリに配置されている型にする場合は、完全修飾名に型の名前、アセンブリの名前、バージョン番号、カルチャ、および公開キー トークンが含まれます。  
  
         次の例の値の設定、 **TypeName**プロパティをソリューションで参照されているアセンブリで定義されている型。  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   BDC オブジェクト モデルで定義されている型にする場合は、完全修飾名に型の名前空間と名前が含まれます。  
  
         次の例の値の設定、 **TypeName**プロパティを BDC オブジェクト モデルの型。  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  **BDC メソッドの詳細**ウィンドウで、型記述子の一覧を開き、クリックして**編集**です。  
  
     **BDC エクスプ ローラー**ウィンドウが開きます。  
  
4.  **BDC エクスプ ローラー**型記述子のショートカット メニューを開きを選択し、**型記述子の追加**です。  
  
     そのエンティティ型記述子の子として新しい型記述子が追加されます。 その型記述子をフィールドとして構成します。  
  
5.  手順 4. を繰り返して、エンティティの各フィールドに対応する子の型記述子を追加します。  
  
### <a name="to-define-a-collection-of-entities"></a>エンティティのコレクションを定義するには  
  
1.  **BDC メソッドの詳細**ウィンドウで、使用するパラメーターの型記述子を選択します。  
  
2.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。  
  
3.  **プロパティ**ウィンドウで、設定、**名前**プロパティをエンティティを記述する名前に (たとえば:**連絡先**)。  
  
4.  設定、 **IsCollection**プロパティを**True**です。 これは、この型記述子がエンティティのコレクションであることを表します。  
  
5.  設定、 **TypeName**プロパティへの参照を表す文字列を<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、およびエンティティを表す型の完全修飾名。 この型は、プロジェクト内のクラスにすることも、ソリューションで参照されているアセンブリで定義されている型にすることも、BDC オブジェクト モデルで定義されている型にすることもできます。  
  
    -   プロジェクトのクラスは、下矢印を選択 の横に、 **TypeName**プロパティを選択、**現在のプロジェクト** タブで、プロジェクトのクラスを選択し、表示されるダイアログ ボックス。  
  
         完全修飾名には、クラスの名前空間および名前と、LOB システムの名前が含まれます。  
  
         次の例の値の設定、 **TypeName**プロパティをプロジェクト内のクラスのコレクション。  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace` ` 。BdcModel1.Contact、BdcModel1]'  
  
    -   ソリューション内のアセンブリに配置されている型にする場合は、完全修飾名に型の名前、アセンブリの名前、バージョン番号、カルチャ、および公開キー トークンが含まれます。  
  
         次の例の値の設定、 **TypeName**プロパティをソリューションで参照されているアセンブリ内の型のコレクション。  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact、myAssemblyName、バージョン = 4.0.0.0、Culture = neutral, PublicKeyToken = b77a5c561934e089]'  
  
    -   BDC オブジェクト モデルで定義されている型にする場合は、完全修飾名に型の名前空間と名前のみが含まれます。  
  
         次の例の値の設定、 **TypeName**プロパティを BDC オブジェクト モデルで定義された型のコレクション。  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'  
  
6.  **BDC メソッドの詳細**ウィンドウで、型記述子の一覧を開き、クリックして**編集**です。  
  
     **BDC エクスプ ローラー**ウィンドウが開きます。  
  
7.  **BDC エクスプ ローラー**型記述子のショートカット メニューを開きを選択し、**型記述子の追加**です。  
  
     そのコレクション型記述子の子として新しい型記述子が追加されます。 その型記述子をエンティティとして構成します。  
  
## <a name="see-also"></a>関連項目  
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: エンティティをモデルに追加します。](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスの定義](../sharepoint/how-to-define-a-method-instance.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  