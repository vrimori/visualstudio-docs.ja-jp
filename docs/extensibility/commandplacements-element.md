---
title: CommandPlacements 要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21978fef22f704c30de2859725fb2f5e704fcefc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886359"
---
# <a name="commandplacements-element"></a>CommandPlacements 要素
CommandPlacements 要素には、CommandPlacement 要素とその他の CommandPlacements グループがグループ化します。  
  
 CommandPlacements 要素は省略可能です。 コマンド、グループ、またはメニューする必要がありますが含まれていない場合、2 次拠点にでは、このセクションを含める必要はありません、 *.vsct*ファイル。  
  
## <a name="syntax"></a>構文  
  
```xml  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|CommandPlacements|CommandPlacement 要素をグループ化し、他の CommandPlacements グループ化します。|  
|[CommandPlacement 要素](../extensibility/commandplacement-element.md)|1 つ以上のグループまたはメニューに含まれるには、ボタン、グループ、およびメニューを使用できます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|コマンドを表すすべての要素を定義します。|  
  
## <a name="example"></a>例  
  
```xml  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>関連項目  
 [CommandPlacement 要素](../extensibility/commandplacement-element.md)   
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)