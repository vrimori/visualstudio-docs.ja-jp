---
title: 要素の親 |Microsoft Docs
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
ms.openlocfilehash: 9a66f9fff773fb9a9542de13ceb97ad8732c319b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39635857"
---
# <a name="parent-element"></a>親要素
ボタンやコンボ ボックスの親のみグループがあります。 メニューまたはグループの親には、他のメニューまたはグループがあります。 [CommandPlacement 要素](../extensibility/commandplacement-element.md)、この要素が必要です。 その他のすべてのインスタンスでは省略可能です。 この要素を省略した場合、親の`Group_Undefined:0`暗黙的に指定されます。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 GUID GUID と ID コマンドの識別子です。|  
|ID|必須。 GUID ID と ID コマンドの識別子です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|統合開発環境 (IDE) には、VSPackage を提供するコマンドを表すすべての要素を定義します。 たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックス。|  
|[Buttons 要素](../extensibility/buttons-element.md)|グループ[ボタン要素](../extensibility/button-element.md)要素。|  
|[Menus 要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
|[Groups 要素](../extensibility/groups-element.md)|VSPackage のコマンド グループを定義するエントリが含まれています。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)