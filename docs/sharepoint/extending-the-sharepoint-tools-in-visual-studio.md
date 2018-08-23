---
title: Visual Studio での SharePoint ツールの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 312c216f3670599653ddc6833f3e8f0e5cf5a8d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42625925"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Visual Studio の SharePoint ツールを拡張します。
  Visual Studio の SharePoint ツールでは、多くのアプリケーション開発シナ リオの要件を満たします。 ただし、か、他の開発者が必要とする機能が常に提供されるとはないを見つけることがあります。 このような場合は、必要な機能を作成する SharePoint ツールを拡張できます。

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint ツールを拡張する方法
 SharePoint プロジェクト システムを拡張して、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウ。

### <a name="extend-the-sharepoint-project-system"></a>SharePoint プロジェクト システムを拡張します。
 Visual Studio には、プロジェクト テンプレートと SharePoint ソリューションの作成に使用できる項目テンプレートのセットが含まれています。 たとえば、イベント レシーバー、リスト定義、ワークフロー、および Web パーツのテンプレートがあります。 ただし、フィールドまたはカスタム アクションなどの SharePoint コンポーネントを作成するための SharePoint プロジェクト アイテムの独自の型を定義することもできます。 Visual Studio で、既にインストールされている SharePoint プロジェクト項目の種類の拡張機能を作成することもでき、SharePoint プロジェクトの拡張機能を作成することができます。

 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張](../sharepoint/extending-the-sharepoint-project-system.md)します。

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。
 Visual Studio で使用することができます、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**階層ツリー ビューで 1 つのコンポーネントの多くまたは複数のローカル SharePoint サイトを表示するウィンドウ。 拡張することも、 **SharePoint 接続**次の方法でノード。

-   独自のノードを追加します。 これは、既定で表示されていない SharePoint サイトのコンポーネントを表示する場合に便利です。

-   既存のノードを拡張します。 たとえば、新しい子ノードを追加するには、既存のノードにまたはノードにショートカット メニュー項目を追加し、開発者がメニュー項目をクリックしたときにタスクを実行します。

 詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。

## <a name="development-computer-requirements"></a>開発コンピューターの要件
 SharePoint ツールの拡張機能を作成するには、開発用コンピューターに Visual Studio で SharePoint ソリューションを作成するため、同じ要件を満たす必要があります。

 インストールすることをお勧め、[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]します。 SDK には、プロジェクト テンプレートと Visual Studio を拡張するのに使用できるツールが含まれています。 具体的には、SDK には、Visual Studio Extension (VSIX) パッケージを簡単に作成する際のプロジェクト テンプレートが含まれています。 VSIX パッケージは、Visual Studio で Visual Studio 拡張機能をデプロイすることをお勧めします。 すべての SharePoint ツール拡張機能は、VSIX パッケージを使用してデプロイする必要があります。 このドキュメントのチュートリアルのすべてがあると、[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]インストールします。

 Visual Studio SDK をインストールするを参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)します。 Visual Studio 拡張機能の詳細については、次を参照してください。 [Visual Studio 拡張機能の開発を開始しています](../extensibility/starting-to-develop-visual-studio-extensions.md)します。

## <a name="see-also"></a>関連項目

- [ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)
- [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [プログラミングの概念と機能の SharePoint ツール拡張機能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [参照&#40;の SharePoint ツールの拡張性&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio の SharePoint ツールの拡張機能をデバッグします。](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio の SharePoint ツールの拡張機能をデプロイします。](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)