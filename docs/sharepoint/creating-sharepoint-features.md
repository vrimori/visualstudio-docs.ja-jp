---
title: SharePoint フィーチャーの作成 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55b1b3f2f243a6c4d35a4c1effbb4ca759abd9d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842883"
---
# <a name="create-sharepoint-features"></a>SharePoint の機能を作成します。
  SharePoint 機能を使用すると、展開が容易に関連の SharePoint プロジェクト アイテムのグループします。 機能の作成、スコープを設定、およびその他の機能を SharePoint フィーチャー デザイナーを使用して依存関係としてマークできます。 デザイナーには、各機能を説明する XML ファイルには、マニフェストも生成されます。  
  
## <a name="add-features-to-the-sharepoint-solution"></a>SharePoint ソリューションに機能を追加します。
 ソリューション エクスプ ローラーまたはパッケージング エクスプ ローラーを使用して、SharePoint ソリューションに機能を追加できます。 機能を追加するのにには、次のメソッドのいずれかを使用できます。  
  
-   **ソリューション エクスプ ローラー**、ショートカット メニューを開き**機能**を選び、**機能の追加**します。  
  
-   **パッケージング エクスプ ローラー**、パッケージのショートカット メニューを開き、選択し、**機能の追加**します。  
  
## <a name="using-the-feature-designer"></a>フィーチャー デザイナーを使用します。
 SharePoint ソリューションは、ソリューション エクスプ ローラーで、そのフィーチャー ノードでグループ化された 1 つまたは複数の SharePoint 機能を含めることができます。 各機能には、独自**フィーチャー デザイナー**機能プロパティのカスタマイズを行えます。 詳細については、「[方法 :SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)します。 いずれかの別の機能を区別するために、タイトル、説明、バージョン、およびスコープなどの機能のプロパティを構成できます。  
  
### <a name="feature-designer-options"></a>デザイナー オプションの機能
 機能を作成した後は、それをカスタマイズするのにフィーチャー デザイナーを使用できます。  
  
 次の表では、フィーチャーのデザイナーに表示される機能のプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|タイトル|任意。 設定されている機能の既定のタイトル*SolutionName* *FeatureName*します。|  
|説明|任意。 SharePoint 機能の説明です。|  
|スコープ|必須。 使用して、機能が作成された場合**ソリューション エクスプ ローラー**既定で Web にスコープが設定されます。<br /><br /> -ファーム:サーバー ファーム全体の機能を有効にします。<br /><br /> サイト:サイト コレクション内のすべての web サイトの機能を有効にします。<br /><br /> Web:特定の web サイトの機能を有効にします。<br /><br /> -Web アプリケーション:Web アプリケーション内のすべての web サイトの機能を有効にします。|  
|[ソリューション内の項目]|フィーチャーに追加できるすべての SharePoint アイテム。|  
|フィーチャー内の項目|フィーチャーに追加されている SharePoint プロジェクト アイテム。|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>SharePoint プロジェクト項目追加および削除
 展開用に SharePoint 機能を追加する SharePoint プロジェクト項目を選択できます。 使用して、**フィーチャー デザイナー**してフィーチャー マニフェストの追加と機能に項目を削除します。 詳細については、「[方法 :項目を SharePoint の機能を追加および削除](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)します。  
  
## <a name="add-feature-dependencies"></a>機能の依存関係を追加します。
 機能をアクティブ化する前に、SharePoint サーバーが特定の機能をアクティブにするために、フィーチャー マニフェストを構成できます。 など、SharePoint の機能は、機能またはデータのための他の機能に依存する場合、SharePoint サーバーできますまずのフィーチャーが依存する機能をアクティブ化します。 詳細については、「[方法 :追加および削除機能の依存関係](../sharepoint/how-to-add-and-remove-feature-dependencies.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint フィーチャーをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: 項目を SharePoint の機能を追加および削除](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [方法: 追加および削除機能の依存関係](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
