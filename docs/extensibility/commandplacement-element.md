---
title: CommandPlacement 要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5d694f6ed12d3fd7d531ec6a0a01ec70a826561
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941360"
---
# <a name="commandplacement-element"></a>CommandPlacement 要素
CommandPlacement 要素では、ボタン、グループ、および 1 つ以上のグループまたはメニューに含まれるメニューを使用します。 CommandPlacement 要素を使用すると、ユーザー インターフェイスの外観を変更するには、これらの項目を完全に再定義する必要はありません。  
  
 詳細については、次を参照してください。[ボタンの再利用可能なグループ作成](../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 定義されている、コマンド セットの guid、 [Symbols 要素](../extensibility/symbols-element.md)します。|  
|ID|必須。 メニューのグループ、または配置するで定義されているコマンドの id、`Symbols Element`します。|  
|priority|必須。 その親要素で項目の表示位置を決定します。|  
|条件|任意。 参照してください[条件付き Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|必須。 メニューまたはグループを配置する項目をホストします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandPlacements 要素](../extensibility/commandplacements-element.md)|CommandPlacements および CommandPlacement 要素のグループを指定します。|  
  
## <a name="example"></a>例  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>関連項目  
 [CommandPlacements 要素](../extensibility/commandplacements-element.md)   
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
