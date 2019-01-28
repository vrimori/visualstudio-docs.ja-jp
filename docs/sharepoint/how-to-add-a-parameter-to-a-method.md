---
title: '方法: メソッドにパラメーターを追加します |。Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d55c345d9cd0e57d7af2ed359cf4bd9a4f06cd9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868119"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>方法: メソッドにパラメーターを追加します。
  メソッドに情報を渡すか、メソッドから情報を返す、パラメーターを使用します。 すべてのメソッドには、少なくとも 1 つのパラメーターが必要です。 作成する方法の種類をサポートするためにパラメーターを設計する方法の詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
 メソッドにパラメーターを追加すると、Visual Studio は、プロジェクト内のモデル ファイルの XML にパラメーター要素を追加します。 Parameter 要素の属性に関する詳細については、次を参照してください。[パラメーター](http://go.microsoft.com/fwlink/?LinkId=169284)します。  
  
### <a name="to-add-a-parameter-to-a-method"></a>メソッドにパラメーターを追加するには  
  
1.  メソッドをエンティティに追加します。  
  
2.  メニュー バーで、**ビュー** > **その他の Windows** > **BDC メソッドの詳細**します。  
  
     **BDC メソッドの詳細**ウィンドウが開きます。 詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)します。  
  
3.  **BDC メソッドの詳細**ウィンドウは、メソッドのノードを展開し、展開、**パラメーター**ノード。  
  
4.  **パラメーターを追加**一覧で、選択**パラメーターの作成**です。  
  
     下に新しいパラメーターが表示されます、**パラメーター**ノード。  
  
5.  メニュー バーで、**ビュー** > **プロパティ ウィンドウ**します。  
  
6.  **プロパティ**ウィンドウで、設定、**名前**プロパティにとって意味のある任意の名前にします。 たとえば、メソッドが顧客に返される場合は、メソッドを名前可能性があります**GetCustomers**します。  
  
7.  **BDC メソッドの詳細**ウィンドウを選択し、開き、パラメーターの方向に表示される一覧**で**、 **InOut**、 **アウト**、または**返す**します。  
  
     作成する型のメソッドを選択する方向についての詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
8.  パラメーターの型記述子を変更します。 詳細については、「[方法 :パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)します。  
  
## <a name="see-also"></a>関連項目
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: エンティティ モデルを追加します。](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法: パラメーターの型記述子を定義します。](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [方法: メソッド インスタンスを定義します。](../sharepoint/how-to-define-a-method-instance.md)   
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)  
