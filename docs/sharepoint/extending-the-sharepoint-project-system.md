---
title: SharePoint プロジェクト システムの拡張 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51449003457ecd09e7dca7bc579d652c94a592e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891113"
---
# <a name="extend-the-sharepoint-project-system"></a>SharePoint プロジェクト システムを拡張します。
  SharePoint ソリューションを作成するには、Visual Studio のプロジェクト テンプレートと項目テンプレートのセットを使用します。 これらのテンプレートは、多くの開発シナ リオの要件を満たすが、場合によっては、必要な機能を提供しないを検出する可能性があります。 このような場合は、SharePoint プロジェクト システムを拡張することができます。  
  
## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint プロジェクト システムの概要
 SharePoint プロジェクト システムは、基本的なコンポーネントのに基づいて*SharePoint プロジェクト アイテム*します。 SharePoint プロジェクト アイテムは、リスト定義、Web パーツ、またはコンテンツの種類など、1 つの SharePoint カスタマイズを表します。  
  
 SharePoint プロジェクトは、1 つまたは複数の SharePoint プロジェクト項目が含まれる Visual Studio のプロジェクトです。 SharePoint プロジェクトには、機能と展開のパッケージにプロジェクト項目をグループ化する方法を定義する追加のコンポーネントも含まれます。  
  
 SharePoint プロジェクト項目および SharePoint プロジェクトの内容に関する詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>SharePoint プロジェクト システムを拡張する方法
 SharePoint プロジェクト システムは、次の方法で拡張できます。  
  
-   独自の SharePoint プロジェクト項目の種類を定義し、新しい項目テンプレート、または Visual Studio のプロジェクト テンプレートに関連付けます。 たとえば、カスタム アクションまたはフィールドを作成するため、SharePoint プロジェクト項目の種類を定義できます。 詳細については、次を参照してください。[カスタム SharePoint プロジェクト項目の種類を定義する](../sharepoint/defining-custom-sharepoint-project-item-types.md)します。  
  
-   Visual Studio で既にインストールされている SharePoint プロジェクト項目の種類を拡張します。 内のプロジェクト項目にショートカット メニュー項目を追加するなど、**ソリューション エクスプ ローラー**および開発者がメニュー項目を選択すると、プロジェクト項目をカスタマイズします。 詳細については、次を参照してください。[拡張の SharePoint プロジェクト アイテム](../sharepoint/extending-sharepoint-project-items.md)します。  
  
-   SharePoint プロジェクトを拡張します。 たとえば、項目が追加されたり、SharePoint プロジェクトから削除されたときに、特定のタスクを実行するイベント ハンドラーを追加することができます。 詳細については、次を参照してください。[拡張の SharePoint プロジェクト](../sharepoint/extending-sharepoint-projects.md)します。  
  
-   SharePoint プロジェクト アイテムと SharePoint プロジェクトのパッケージ化と配置の動作を拡張します。 たとえば、追加のカスタム タスクを実行するには、Visual Studio は、特定の展開手順を実行するとき、または配置または取り消しプロジェクトするときに実行する独自の展開ステップを作成できます。 詳細については、次を参照してください。 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)します。  
  
## <a name="common-development-tasks"></a>一般的な開発タスク
 SharePoint プロジェクト システムの拡張機能では、次の一般的なタスクを実行できます。  
  
-   プロジェクト項目を含む、いくつかの異なる種類のプロジェクト ファイルでは、カスタムの文字列データを保存します。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でデータを保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)します。  
  
-   SharePoint プロジェクト システムで Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデル内の対応するオブジェクトをオブジェクトに変換またはその逆です。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類の間の変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)します。  
  
## <a name="see-also"></a>関連項目
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目を拡張します。](../sharepoint/extending-sharepoint-project-items.md)   
 [SharePoint プロジェクトを拡張します。](../sharepoint/extending-sharepoint-projects.md)   
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint プロジェクト システムの拡張機能でデータを保存します。](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換します。](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Visual Studio の SharePoint ツールを拡張します。](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint ツール拡張機能におけるプログラミングに関する概念および特徴](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
