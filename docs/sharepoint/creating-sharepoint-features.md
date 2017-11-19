---
title: "SharePoint フィーチャーの作成 |Microsoft ドキュメント"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
ms.assetid: 2e211fb3-94f4-4921-ba77-2ba6717a3e41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8f78a12aa70c3c7042a821a737485da963f7a56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-features"></a>SharePoint フィーチャーの作成
  SharePoint 機能を使用して、展開が容易に関連する SharePoint プロジェクト項目をグループ化することができます。 機能を作成、スコープの設定、およびその他の機能を SharePoint フィーチャー デザイナーを使用して、依存関係としてマークできます。 デザイナーには、各機能を記述する XML ファイルである、マニフェストも生成されます。  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>SharePoint ソリューションに機能を追加します。  
 SharePoint ソリューションに機能を追加するには、ソリューション エクスプ ローラーまたはパッケージング エクスプ ローラーを使用します。 機能を追加するのにには、次のいずれかを使用できます。  
  
-   **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**機能**を選択し**フィーチャーの追加**です。  
  
-   **パッケージング エクスプ ローラー**をパッケージのショートカット メニューを開きを選択し、**フィーチャーの追加**です。  
  
## <a name="using-the-feature-designer"></a>フィーチャー デザイナーを使用  
 SharePoint ソリューションには、ソリューション エクスプ ローラーで、そのフィーチャー ノードの下でグループ化されている 1 つまたは複数の SharePoint 機能を含めることができます。 各機能には、独自**フィーチャー デザイナー**フィーチャーのプロパティのカスタマイズを行えます。 詳細については、次を参照してください。[する方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)です。 いずれかの別の機能を区別するためには、タイトル、説明、バージョン、およびスコープなどの機能のプロパティを構成できます。  
  
### <a name="feature-designer-options"></a>フィーチャー デザイナーのオプション  
 機能を作成した後は、それをカスタマイズするのにフィーチャー デザイナーを使用できます。  
  
 次の表では、フィーチャー デザイナーに表示される機能のプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|タイトル|省略可能です。 設定されている機能の既定のタイトル*SolutionName**FeatureName*です。|  
|説明|省略可能です。 SharePoint の機能の説明です。|  
|スコープ|必須です。 使用して、機能を作成する場合**ソリューション エクスプ ローラー**スコープが既定では Web に設定します。<br /><br /> -ファーム:、サーバー ファーム全体の機能が有効にします。<br /><br /> サイト:、すべての web サイトのサイト コレクション機能が有効にします。<br /><br /> -Web:、特定の web サイトの機能が有効にします。<br /><br /> -WebApplication:、すべての web サイトの web アプリケーションの機能が有効にします。|  
|[ソリューション内の項目]|フィーチャーに追加できるすべての SharePoint アイテムです。|  
|フィーチャー内の項目|フィーチャーに追加されている SharePoint プロジェクト項目です。|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>追加して、SharePoint プロジェクト項目の削除  
 SharePoint プロジェクト項目を展開するための SharePoint 機能を追加することを選択することができます。 使用して、**フィーチャー デザイナー**して、フィーチャーのマニフェストの追加と、機能に項目を削除します。 詳細については、次を参照してください。[する方法: 追加および SharePoint フィーチャーの項目を削除する](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)です。  
  
## <a name="adding-feature-dependencies"></a>機能の依存関係を追加します。  
 フィーチャー マニフェストは、機能をアクティブ化する前に、SharePoint サーバーが特定の機能をアクティブにできるように構成できます。 たとえば、SharePoint の機能は、機能やデータの他の機能に依存する場合、SharePoint サーバーことができますまずの機能が依存する機能をアクティブ化するします。 詳細については、次を参照してください。[する方法: 追加および機能の依存関係を削除する](../sharepoint/how-to-add-and-remove-feature-dependencies.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: 追加および SharePoint フィーチャーの項目を削除します。](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [方法: フィーチャーの依存関係を追加および削除する](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  