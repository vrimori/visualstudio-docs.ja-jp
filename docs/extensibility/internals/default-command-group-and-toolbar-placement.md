---
title: 既定のコマンド、グループ、およびツールバーの配置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: da5716460c428098b2b6cc3bb78a51c3831201b2
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498231"
---
# <a name="default-command-group-and-toolbar-placement"></a>既定のコマンド、グループ、およびツールバーの配置
製品の統一性と安定性は、UI は既定では、コマンドの特定のグループを表示し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドとコマンドのグループの定義を提供します。 Vspackage は、標準のコマンドおよびコマンド グループにも使用できます。  
  
 コマンドの既定のグループが 3 つのカテゴリに分類されます。 IDE コマンド、コマンドの製品、およびエディター コマンド。  
  
## <a name="default-ide-commands"></a>既定の IDE コマンド  
 既定の IDE ツールバーには、コマンドに含まれているすべての製品と共有が含まれています。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 など、汎用的なプロジェクトの操作に関連するコマンドが含まれます、**保存**コマンドと**項目の追加**コマンド。 Vspackage に追加またはこのツールバーで、1 つの例外から減算する必要がありますいない: かどうかには、製品または VSPackage は、新しいツール ウィンドウを追加し、ウィンドウで使用可能なツール ウィンドウの一覧に追加する必要があります、**ビュー**メニュー。 新しい製品や Vspackage は、独自のツールバーを追加できます。  
  
## <a name="default-product-commands"></a>既定の製品コマンド  
 各製品には、重要なが含まれており、よく使用されるコマンドを独自の既定のツールバーを使用して IDE を提供できます。 ただし、既存のメニューおよびツールバーが可能な限りを使用して、必要に応じて、他のタスク固有のツールバーに追加し、最適なは。  
  
 ツールバーの優先順位フィールドは、行の位置を決定します。 0 個の優先度、メニュー バーの下に 3 番目の行 (行 3) で、ツールバーを配置する (1 行) と**標準**ツールバー (2 行目)。 したがって、行の他のツールバーが表示されます (優先度 + 3)。 後続のツールバーは; スペースがある場合、同じ行に配置されます。それ以外の場合、次の行に、自動的に移動するされます。  
  
## <a name="default-editor-commands"></a>既定のエディター コマンド  
 カスタム エディターを提供する VSPackage は、既定のツールバーで、最も重要な含み、そのエディターでよく使用されるコマンドを提供します。 エディターがアクティブであり、エディターがアクティブでない場合に非表示にするときに、エディター ツールバーが表示されます。 この可視性が制御されます、`VisibilityConstraints`の要素、 *.vsct*ファイル。  
  
 エディターのツールバーは、IDE と製品のツールバーの下に配置する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)