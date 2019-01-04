---
title: エンティティ間のアソシエーションを作成する |Microsoft Docs
ms.date: 02/02/2017
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
ms.openlocfilehash: 134b477cdc199d85c983633a2a5996d113420443
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842980"
---
# <a name="create-an-association-between-entities"></a>エンティティ間のアソシエーションを作成します。
  関連付けを作成して、ビジネス データ接続 (BDC) モデルのエンティティ間のリレーションシップを定義することができます。 Visual Studio では、各関連付けについての情報をモデルのコンシューマーに提供するメソッドを生成します。 これらのメソッドは、SharePoint web パーツ、リスト、またはユーザー インターフェイス (UI) でデータ間の関係を表示するカスタム アプリケーションで使用できます。  
  
## <a name="create-an-association"></a>関連付けを作成します。
 選択して、アソシエーションを作成、**アソシエーション**Visual Studio でのコントロール**ツールボックス**、最初のエンティティ (ソース エンティティと呼ばれます) を選択し、別のエンティティを選択し (と呼ばれる、転送先エンティティの場合)。 関連付けの詳細を定義することができます、**関連付けエディター**します。 詳細については、「[方法 :エンティティ間のアソシエーションを作成する](../sharepoint/how-to-create-an-association-between-entities.md)します。  
  
## <a name="association-methods"></a>関連付けメソッド
 SharePoint ビジネス データ web パーツなどのアプリケーションでは、エンティティのサービス クラスでメソッドを呼び出して、関連付けを使用します。 選択して、エンティティのサービス クラスにメソッドを追加することができます、**関連付けエディター**します。  
  
 既定で、**関連付けエディター**元とコピー先のエンティティ、アソシエーションのナビゲーション メソッドを追加します。 ソース エンティティ、アソシエーションのナビゲーション メソッドには、移行先のエンティティの一覧を取得するコンシューマーができます。 転送先エンティティで、アソシエーションのナビゲーション メソッドでは、転送先エンティティに関連するソース エンティティを取得するコンシューマーを使用します。  
  
 適切な情報を返すには、各メソッドにコードを追加する必要があります。 他の種類の高度なシナリオをサポートするメソッドを追加することもできます。 これらの各方法の詳細については、次を参照してください。[サポートされている操作](http://go.microsoft.com/fwlink/?LinkId=169286)します。  
  
## <a name="types-of-associations"></a>関連付けの種類
 2 つの種類のアソシエーションを作成するには、BDC デザイナーに: 外部キーに基づくアソシエーションおよび外部キーを使用しないアソシエーション。  
  
### <a name="foreign-key-based-association"></a>外部キー ベースの関連付け
 外部キーに基づくアソシエーションを作成するには、転送先エンティティで定義されている記述子を入力するソース エンティティの識別子に関連します。 この関係により、モデルのコンシューマーは、ユーザーの拡張 UI を提供します。 たとえば、ユーザーが、ドロップダウン リストで顧客を表示できる販売注文を作成できるように Outlook でフォームまたは、ユーザーが顧客のプロファイル ページを開くことができるようにする SharePoint での販売注文の一覧。  
  
 外部キーに基づくアソシエーションを作成するには、識別子に関連して、同じ名前と型を共有する記述子を入力します。 間の外部キー ベースの関連付けを作成するなど、`Contact`エンティティと`SalesOrder`エンティティ。 `SalesOrder`エンティティを返します、 `ContactID` Finder または Specificfinder メソッドの戻り値パラメーターの一部として記述子を入力します。 両方の型記述子の表示で、**関連付けエディター**します。 間に外部キーに基づくリレーションシップを作成する、`Contact`エンティティと`SalesOrder`、エンティティを選択して、`ContactID`これらの各フィールドの横にある識別子。  
  
 変換先のエンティティのコレクションを返すソース エンティティの関連付けのナビゲーター メソッドにコードを追加します。 次の例では、取引先担当者の販売注文を返します。  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 ソースのエンティティを返す転送先エンティティの関連付けのナビゲーター メソッドにコードを追加します。 次の例では、販売注文に関連する連絡先を返します。  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>外部キーなしの関連付け
 アソシエーションを作成するにはフィールド型記述子に識別子を割り当てられません。 ソース エンティティは転送先エンティティとの直接的なリレーションシップを持っていない場合に、このような関連付けを作成します。 たとえば、`SalesOrderDetail`テーブルに主キーにマップされる外部キーがありません、`Contact`テーブル。  
  
 内の情報を表示する場合、`SalesOrderDetail`に関連するテーブルを`Contact`、間の外部キーを使用しない関連付けを作成することができます、`Contact`エンティティと`SalesOrderDetail`エンティティ。  
  
 アソシエーションのナビゲーション方法で、`Contact`エンティティ、戻り値、`SalesOrderDetail`エンティティ、テーブルを結合することで、またはストアド プロシージャを呼び出すことによって。  
  
 次の例では、テーブルを結合してすべての販売注文の詳細を返します。  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 アソシエーションのナビゲーション メソッドで、`SalesOrderDetail`エンティティを返す、関連する`Contact`します。 次に例を示します。  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: エンティティ間のアソシエーションを作成します。](../sharepoint/how-to-create-an-association-between-entities.md)  
