---
title: "IDSymbol 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d05dd013be9a3d6c4a173a5c7abc7a01ef2d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idsymbol-element"></a>IDSymbol 要素
`IDSymbol`要素には、メニューのグループ、またはコマンドを表す GUID:ID のペアの ID が含まれています。 GUID は、親から取得`GuidSymbol`要素。 `IDSymbol`要素には、`name`に含まれていると、ID のフレンドリ名を提供する属性、`value`属性。  
  
## <a name="syntax"></a>構文  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|必須です。 ID シンボルの名前です。|  
|値|必須です。 ID シンボルの数値の ID 値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[GuidSymbol 要素](../extensibility/guidsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID のペアの GUID が含まれています。 複数の `IDSymbol` 要素をグループ化します。|  
  
## <a name="remarks"></a>コメント  
 各`IDSymbol`内の要素を指定した`GuidSymbol`要素は、一意でなければなりません`value`です。 ただし、`IDSymbol`別の親を持っていれば、パッケージで同じ値を持つ要素が存在できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)