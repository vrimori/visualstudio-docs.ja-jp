---
title: "CommandPlacement 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6a5c8d9220b0cd2c0dddfee283d222f4efb9ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="commandplacement-element"></a>CommandPlacement 要素
CommandPlacement 要素は、1 つ以上のグループまたはメニューに含まれるには、ボタン、グループ、およびメニューを使用します。 CommandPlacement 要素を使用すると、ユーザー インターフェイスの外観を変更するのには、これらの項目を完全に再定義するはありません。  
  
 詳細については、次を参照してください。[ボタンの再利用可能なグループの作成](../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 定義されているコマンド セットの guid、[シンボル要素](../extensibility/symbols-element.md)です。|  
|ID|必須。 メニューのグループ、または配置されるで定義されているコマンドの id、`Symbols Element`です。|  
|priority|必須。 その親要素内の項目の visual の位置を決定します。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|必須。 メニューまたはグループを配置する項目をホストしています。|  
  
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
  
## <a name="see-also"></a>参照  
 [CommandPlacements 要素](../extensibility/commandplacements-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)