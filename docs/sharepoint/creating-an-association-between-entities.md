---
title: エンティティ間の関連付けを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 293441e93c38a65ca343b021b2bf19c5a56ac7c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-association-between-entities"></a>エンティティ間の関連付けの作成
  関連付けを作成することで、ビジネス データ接続 (BDC) モデルのエンティティ間のリレーションシップを定義することができます。 Visual Studio では、各アソシエーションに関する情報をモデルのコンシューマーに提供するメソッドを生成します。 これらのメソッドは、SharePoint web パーツ、リスト、またはユーザー インターフェイス (UI) でデータ間の関係を表示するカスタム アプリケーションで使用できます。  
  
## <a name="creating-an-association"></a>関連付けの作成  
 選択して関連付けを作成、**アソシエーション**Visual Studio でのコントロール**ツールボックス**最初のエンティティ (ソース エンティティと呼ばれます) を選択し、2 番目のエンティティを選択し、(と呼ばれる、参照先エンティティの場合)。 関連付けの詳細を定義することができます、 **関連付けエディター**です。 詳細については、次を参照してください。[する方法: エンティティ間の関連付けを作成する](../sharepoint/how-to-create-an-association-between-entities.md)です。  
  
## <a name="association-methods"></a>関連付けメソッド  
 SharePoint ビジネス データ web パーツなどのアプリケーションでは、エンティティのサービス クラスでメソッドを呼び出して関連付けを使用します。 選択するエンティティのサービス クラスにメソッドを追加することができます、 **関連付けエディター**です。  
  
 既定では、 **関連付けエディター**元とコピー先のエンティティに関連付けナビゲーション メソッドを追加します。 ソース エンティティ、アソシエーション ナビゲーション メソッドは、移行先のエンティティの一覧を取得するコンシューマーを使用できます。 転送先エンティティで、アソシエーション ナビゲーション メソッドは、参照先のエンティティに関連するソース エンティティを取得するコンシューマーを使用できます。  
  
 これらの各メソッドを適切な情報を返すには、コードを追加する必要があります。 他の種類の高度なシナリオをサポートするメソッドを追加することもできます。 これらの各方法の詳細については、次を参照してください。[サポートされている操作](http://go.microsoft.com/fwlink/?LinkId=169286)です。  
  
## <a name="types-of-associations"></a>関連付けの種類  
 BDC デザイナーでの関連付けの 2 つの種類を作成することができます。 外部キーに基づくアソシエーションとキーを使用しない外部のアソシエーション。  
  
### <a name="foreign-key-based-association"></a>外部キーに基づく関連付け  
 外部キー ベースの関連付けを作成するには、関連する参照先エンティティで定義されている記述子を入力するソース エンティティの識別子。 このリレーションシップにより、モデルのコンシューマーは、ユーザーの拡張 UI を提供します。 たとえば、ユーザーがに対して、ドロップダウン リストで顧客を表示する販売注文を作成できるようにする、Outlook でフォームまたは、ユーザーが顧客のプロファイル ページを開くことができるようにする SharePoint での販売注文の一覧です。  
  
 外部キーに基づく関連付けを作成するには、識別子を関連し、同じ名前よぶ型を共有する記述子を入力します。 間の外部キー ベースの関連付けを作成するなど、`Contact`エンティティと`SalesOrder`エンティティです。 `SalesOrder`エンティティを返します、 `ContactID` Finder または Specificfinder メソッドの戻り値パラメーターの一部として記述子を入力します。 両方の型記述子の表示で、 **関連付けエディター**です。 間に外部キーに基づくリレーションシップを作成する、`Contact`エンティティと`SalesOrder`、エンティティを選択して、`ContactID`これらの各フィールドの横にある識別子。  
  
 移行先のエンティティのコレクションを返すソース エンティティの関連付けナビゲーター メソッドにコードを追加します。 次の例では、取引先担当者の販売注文を返します。  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 ソース エンティティを返す転送先エンティティの関連付けナビゲーター メソッドにコードを追加します。 次の例では、販売注文に関連付けられている連絡先を返します。  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>外部キーを使用しない関連付け  
 フィールド型記述子に識別子を割り当てずに、関連付けを作成できます。 ソース エンティティがターゲット エンティティとの直接的なリレーションシップを持っていない場合に、このような関連付けを作成します。 たとえば、`SalesOrderDetail`テーブルに主キーにマップされる外部キーがない、`Contact`テーブル。  
  
 内の情報を表示する場合、`SalesOrderDetail`に関連するテーブル、 `Contact`、間の外部キーを使用しない関連付けを作成することができます、`Contact`エンティティと`SalesOrderDetail`エンティティです。  
  
 アソシエーション ナビゲーション メソッド内で、`Contact`エンティティ、戻り値、`SalesOrderDetail`エンティティ、テーブルを結合することで、またはストアド プロシージャを呼び出すことによってです。  
  
 次の例では、テーブルを結合することで、すべての販売注文の詳細を返します。  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 アソシエーション ナビゲーション メソッド内で、`SalesOrderDetail`エンティティを返す、関連する`Contact`です。 次に例を示します。  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>関連項目  
 [ビジネス データ接続モデルの設計](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: エンティティ間の関連付けを作成します。](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  