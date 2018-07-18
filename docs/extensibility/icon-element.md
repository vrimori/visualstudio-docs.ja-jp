---
title: Icon 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f15dcfec5c89c6bf2b2ae68ea29e18890dc9187e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126878"
---
# <a name="icon-element"></a>Icon 要素
アイコンのタグの guid 属性は、定義済みのビットマップの guid です。  Id 属性は、ビットマップ ストリップのスロットを選択します。 この要素は省略可能です。  この要素を省略した場合の値**guidOfficeIcon:msotcidNoIcon**暗黙的に指定されます。  
  
## <a name="syntax"></a>構文  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 定義済みのビットマップの guid です。|  
|ID|必須。 ビットマップ ストリップのスロットを選択します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし。|なし。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)