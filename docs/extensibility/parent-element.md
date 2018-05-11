---
title: 要素の親 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 795654925a92f3e9ac0718e070e85c0f4f7f21c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="parent-element"></a>Parent 要素
ボタンやコンボ ボックスの親のみグループがあります。 メニューまたはグループの親には、その他のメニューまたはグループがあります。 [CommandPlacement 要素](../extensibility/commandplacement-element.md)、この要素は必須です。 その他のすべてのインスタンスでは省略可能です。 この要素を省略すると、親の`Group_Undefined:0`暗黙的に指定されます。  
  
## <a name="syntax"></a>構文  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 GUID の GUID と ID のコマンド識別子です。|  
|ID|必須。 ID の GUID と ID のコマンド識別子です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|統合開発環境 (IDE) に VSPackage を提供するコマンドを表すすべての要素を定義します。 たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックス。|  
|[Buttons 要素](../extensibility/buttons-element.md)|グループ[ボタン要素](../extensibility/button-element.md)要素。|  
|[Menus 要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
|[Groups 要素](../extensibility/groups-element.md)|VSPackage のコマンドのグループを定義するエントリが含まれています。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)