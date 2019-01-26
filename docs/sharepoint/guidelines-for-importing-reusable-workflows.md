---
title: Guidelines for Importing Reusable Workflows |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 329d38e8c258148830347a506ceef5845c1cf268
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874277"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>再利用可能なワークフローをインポートするためのガイドライン
  SharePoint Designer で作成された再利用可能なワークフローをインポートするには、再利用可能な SharePoint 2010 ワークフローのインポート プロジェクト テンプレートを使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 このテンプレートをインポート、*宣言型**ワークフロー* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-のみ) に変換します、*コード ワークフロー*、これは、いずれかで強化できるワークフロー[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]または[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]コード。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [チュートリアル:SharePoint Designer の再利用可能なワークフローを Visual Studio にインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)します。  
  
 ただし、再利用可能な SharePoint 2010 ワークフローのインポート テンプレートは、ファーム ソリューションのみをインポートすることができます。 サンド ボックス ソリューションとして、ワークフローを展開する場合は、SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用してインポートします。 ただし、これにより、ワークフローをコードに変換することはできませんし、ように変更することはできません。  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>再利用可能なワークフローのインポート テンプレートを使用して再利用可能なワークフローのインポート
 再利用可能な SharePoint 2010 ワークフローのインポート テンプレートを使用して再利用可能なワークフローをインポートする場合は、実行またはその他のようなソリューションを変更する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]が SharePoint のソリューションは、いくつかの項目を手動で修正する必要があります。  
  
### <a name="import-task-forms"></a>タスク フォームをインポートします。
 再利用可能な SharePoint 2010 ワークフローのインポート プロジェクト テンプレートすべての開始との関連付けフォームをインポートしますが、コード ワークフローのスキーマでは、1 つのタスク フォームのみが許可するために、1 つだけタスク フォームをインポートします。 元のワークフロー ソリューションから他のタスク フォームが入れられます、**インポートされたファイルの他の**フォルダー**ソリューション エクスプ ローラー**します。  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用して再利用可能なワークフローのインポート
 SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用して再利用可能なワークフローをインポートする場合は、次の問題を考慮する必要があります。  
  
-   ワークフローをインポートした後は、すぐにデプロイしで実行することができます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を選択して、 **F5**キー。 ただし、インポートされたソリューションでのワークフローで何も変更するを展開して、ワークフローを実行する前に、プロジェクトで要素を手動で修正するがあります。  
  
-   ワークフローは、宣言型であるためにコードを追加することはできません。 コード ワークフローにワークフローを変換する必要がありますにインポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]再利用可能な SharePoint 2010 ワークフローのインポート テンプレートを使用しています。  
  
-   デザイン ビューでワークフロー デザイナー (.xoml) ファイルを編集することができますが勧めソース ビューで、編集すること、ワークフロー デザイナーでの間違ったエラーが表示されるためです。  
  
-   ワークフローでのデバッグは、宣言型のコンテンツに対しては機能しません。 ブレークポイントを設定、[!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)]はヒットしません。  
  
## <a name="import-globally-reusable-workflow-solutions"></a>グローバルに再利用可能なワークフロー ソリューションをインポートします。
 再利用可能な SharePoint 2010 のワークフローのインポート テンプレートを使用してグローバルに再利用可能なワークフローをインポートすることはできません。 グローバルに再利用可能なワークフローをインポートするには、非グローバルに再利用可能なワークフローに変換する必要があるか、SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用する必要があります。  
  
 ワークフローに変換するには、SharePoint Designer でグローバルに再利用可能なワークフローのコピーを作成 (ワークフローのショートカット メニューを開き、して**コピーとして保存**)。 再利用可能な SharePoint 2010 ワークフローのインポート テンプレートを使用して新しい再利用可能なワークフローをインポートし、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
 変更せずに、グローバルに再利用可能なワークフローをインポートするには、SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用します。 このメソッドを使用する場合、ワークフロー コード ワークフローに変換されないと、宣言型ワークフローのまま。  
  
## <a name="see-also"></a>関連項目
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [チュートリアル: SharePoint Designer の再利用可能なワークフローを Visual Studio にインポートします。](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
