---
title: "既定のコマンド、グループ、およびツールバー配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5f1ec42408e4fd7d33d9445ae09252fae8d03db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="default-command-group-and-toolbar-placement"></a>既定のコマンド、グループ、およびツールバーの配置
製品統一性と安定性は、UI は既定では、コマンドの特定のグループを表示および[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドおよびコマンド グループの定義について説明します。 Vspackage は、標準のコマンドおよびコマンド グループにも使用できます。  
  
 コマンドのグループを既定値は 3 つのカテゴリに分類されます。 IDE コマンド、製品コマンド、およびエディター コマンド。  
  
## <a name="default-ide-commands"></a>既定の IDE コマンド  
 既定の IDE ツールバーには、コマンドに含まれているすべての製品と共有が含まれています。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 など、汎用的なプロジェクトの操作に関連するコマンドが含まれます、**保存**コマンドおよび**項目の追加**コマンド。 Vspackage に追加または 1 つの例外で、このツールバーからを減算する必要がありますいない: かどうかには、製品や VSPackage は、新しいツール ウィンドウを追加し、ウィンドウで利用可能なツール ウィンドウの一覧に追加する必要があります、**ビュー**メニュー。 新しい製品や Vspackage は、独自のツールバーを追加できます。  
  
## <a name="default-product-commands"></a>既定の製品コマンド  
 各製品には、重要なが含まれており、頻繁に使用するコマンドを独自の既定のツールバーを使用して IDE を提供できます。 ただし、既存のメニューと可能な限りツールバーを使用して、必要に応じて他のタスク固有のツールバーに追加し、最適なは。  
  
 ツールバーの [優先順位] フィールドでは、行の配置を決定します。 0 個の優先順位、メニュー バーの下に 3 番目の行 (行 3) に、ツールバーを配置する (1 行) と**標準**ツールバー (行 2)。 したがって、行の他のツールバーが表示されます (優先度 + 3)。 ルーム; がある場合、同じ行に対して後続のツールバーを配置します。それ以外の場合、次の行に移動されます自動的に。  
  
## <a name="default-editor-commands"></a>既定のエディター コマンド  
 カスタム エディターを提供する VSPackage には、最も重要なが含まれており、そのエディターでのコマンドを頻繁に使用する既定のツールバーを提供する必要があります。 エディターがアクティブであり、エディターがアクティブでない場合に非表示にするときに、エディターのツールバーが表示されます。 この可視性はによって制御されます、 `VisibilityConstraints Element` .vsct ファイルのです。  
  
 エディターのツールバーは、IDE と製品のツールバーの下に配置する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)