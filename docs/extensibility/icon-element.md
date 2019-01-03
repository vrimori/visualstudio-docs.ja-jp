---
title: Icon 要素 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 475bca35ca1bdc1879301912c7ddd271f369a6ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870009"
---
# <a name="icon-element"></a>Icon 要素
アイコンのタグの guid 属性は、定義されているビットマップの guid です。 `id`属性は、ビットマップ ストリップでスロットを選択します。 この要素は省略可能です。 この要素がない場合の値が含まれている**guidOfficeIcon:msotcidNoIcon**暗黙的に指定されます。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 定義されているビットマップの guid です。|  
|ID|必須。 ビットマップ ストリップでスロットを選択します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし。|なし。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)