---
title: '方法: エンティティ モデルを追加する |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 347728ac4f096359f06ca7823adfcd1b25ff527a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964035"
---
# <a name="how-to-add-an-entity-to-a-model"></a>方法: エンティティ モデルを追加します。
  エンティティを作成するには、Visual Studio からエンティティ コントロールを追加**ツールボックス**ビジネス データ接続 (BDC) をデザイナーにします。  
  
### <a name="to-add-an-entity-to-the-model"></a>モデルにエンティティを追加するには  
  
1.  BDC プロジェクトを作成するか、既存の BDC プロジェクトを開きます。 詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
2.  **ツールボックス**から、 **BusinessDataCatalog**グループで、追加、**エンティティ**コントロールをデザイナーにします。  
  
     デザイナーで新しいエンティティが表示されます。 Visual Studio の追加、`<Entity>`プロジェクト内の BDC モデル ファイルの xml 要素。 エンティティ要素の属性に関する詳細については、次を参照してください。[エンティティ](http://go.microsoft.com/fwlink/?LinkId=169296)します。  
  
3.  デザイナーで、エンティティのショートカット メニューを開き、選択**追加**を選び、**識別子**します。  
  
     エンティティに新しい識別子が表示されます。  
  
    > [!NOTE]  
    >  エンティティとの識別子の名前を変更することができます、**プロパティ**ウィンドウ。  
  
4.  クラスでは、エンティティのフィールドを定義します。 プロジェクトに新しいクラスを追加するか、オブジェクト リレーショナル デザイナー (O/R デザイナー) などの他のツールを使用して作成された既存のクラスを使用します。 次の例では、連絡先をという名前のエンティティ クラスを示します。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>関連項目
 [方法: Creator メソッドを追加します。](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加します。](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加します。](../sharepoint/how-to-add-an-updater-method.md)   
 [方法: Finder メソッドを追加します。](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)  
