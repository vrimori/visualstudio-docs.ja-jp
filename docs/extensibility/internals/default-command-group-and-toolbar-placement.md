---
title: "既定のコマンド、グループ、およびツールバー配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
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
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1d418eea04791d85dd0e8d08fba23abe8dc7e054
ms.lasthandoff: 02/22/2017

---
# <a name="default-command-group-and-toolbar-placement"></a>既定のコマンド、グループ、およびツールバーの配置
製品の統一性と安定性は、UI に既定では、コマンドの特定のグループが表示および[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドおよびコマンド グループの定義について説明します。 VSPackages には、標準のコマンドおよびコマンド グループも使用できます。  
  
 コマンドの既定のグループが&3; つのカテゴリに分類されます。 IDE コマンド、製品コマンド、およびエディター コマンドです。  
  
## <a name="default-ide-commands"></a>既定の IDE コマンド  
 既定の IDE ツールバーには、コマンドに含まれているすべての製品と共有が含まれています。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 などの汎用的なプロジェクトの操作に関連するコマンドが含まれます、**保存**コマンドと**項目の追加**コマンドです。 Vspackages にあるに追加しない、またはこのツールバーで、1 つの例外から減算する必要があります。 場合には、製品または VSPackage は、新しいツール ウィンドウを追加してから、ウィンドウは、利用可能なツール ウィンドウの一覧に追加する必要があります、**ビュー**メニュー。 新しい製品や VSPackages には、独自のツールバーを追加できます。  
  
## <a name="default-product-commands"></a>既定のコマンドの製品  
 各製品には、重要なが含まれており、よく使用されるコマンドを独自の既定のツールバーを使用して IDE を提供できます。 ただし、既存のメニューおよびツールバー可能な限りを使用して、必要に応じて他のタスクに固有のツールバーに追加し、最適なです。  
  
 ツールバーの [優先度] フィールドでは、その行の配置を決定します。 ゼロの優先度、ツールバーをメニュー バーの下に 3 番目の行 (行 3) に配置する (1 行) と**標準**ツールバー (行 2)。 したがって、行の他のツールバーが表示されます (優先度は + 3)。 余裕がある場合、同じ行に対して後続のツールバーが配置されますそれ以外の場合、次の行に移動されるは自動的にします。  
  
## <a name="default-editor-commands"></a>既定のエディター コマンド  
 カスタム エディターを提供する VSPackage では、最も重要なが含まれており、そのエディターでのコマンドを頻繁に使用する既定のツールバーを提供する必要があります。 エディターがアクティブであり、エディターがアクティブでないときに非表示にするときに、エディターのツールバーが表示されます。 この可視性を制御、 `VisibilityConstraints Element` .vsct ファイルのです。  
  
 エディターのツールバーは、IDE と製品のツールバーの下に配置する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
