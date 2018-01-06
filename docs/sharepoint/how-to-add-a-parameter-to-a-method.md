---
title: "方法: メソッドにパラメーターを追加 |Microsoft ドキュメント"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f6810d69628c66a011123250b8e0efb8622f0be7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-parameter-to-a-method"></a>方法 : メソッドにパラメーターを追加する
  メソッドに情報を渡すか、メソッドから情報を返す、パラメーターを使用します。 すべてのメソッドには、少なくとも 1 つのパラメーターが必要です。 作成する方法の種類をサポートするためにパラメーターを設計する方法の詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
 Visual Studio が追加のメソッドにパラメーターを追加すると、`<Parameter>`要素をモデル プロジェクト内のファイル、XML にします。 属性の詳細については、`<Parameter>`要素を参照してください[パラメーター](http://go.microsoft.com/fwlink/?LinkId=169284)です。  
  
### <a name="to-add-a-parameter-to-a-method"></a>メソッドにパラメーターを追加するには  
  
1.  メソッドは、エンティティを追加します。  
  
2.  メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、 **BDC メソッドの詳細**です。  
  
     **BDC メソッドの詳細**ウィンドウが開きます。 詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)です。  
  
3.  **BDC メソッドの詳細**ウィンドウが、メソッドのノードを展開し、展開、**パラメーター**ノード。  
  
4.  **パラメーターを追加**一覧で、選択**パラメーターの作成**です。  
  
     下に新しいパラメーターが表示されます、**パラメーター**ノード。  
  
5.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。  
  
6.  **プロパティ**ウィンドウで、設定、**名前**プロパティを意味のある任意の名前にします。 たとえば、メソッドは、顧客を返しますが場合、は、メソッドを名前可能性があります**GetCustomers**です。  
  
7.  **BDC メソッドの詳細** ウィンドウでは、パラメーターの方向に表示されるリストを開きを選択し、**で**、 **InOut**、 **アウト**、または**返す**です。  
  
     どちらの方向を作成している型のメソッドの選択の詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
8.  パラメーターの型記述子を変更します。 詳細については、次を参照してください。[する方法: パラメーターの型記述子を定義する](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)です。  
  
## <a name="see-also"></a>参照  
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: エンティティをモデルに追加します。](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法: パラメーターの型記述子を定義します。](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [方法: メソッド インスタンスの定義](../sharepoint/how-to-define-a-method-instance.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  