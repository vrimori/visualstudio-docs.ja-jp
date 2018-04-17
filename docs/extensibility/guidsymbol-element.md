---
title: GuidSymbol 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d5e3a3f4d33e166d344669dbeb4bc1a877335f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="guidsymbol-element"></a>GuidSymbol 要素
`GuidSymbol`要素には、メニューのグループ、またはコマンドを表す GUID:ID ペアの GUID が含まれています。 ID に由来する`IDSymbol`内の要素、`GuidSymbol`要素。 `GuidSymbol`要素には、`name`に含まれている GUID のフレンドリ名を提供する属性、`value`属性。  
  
## <a name="syntax"></a>構文  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|必須。 GUID 記号の名前です。|  
|value|必須。 GUID 記号の GUID です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[IDSymbol 要素](../extensibility/idsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID のペアの ID が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Symbols 要素](../extensibility/symbols-element.md)|グループ`GuidSymbol`.vsct ファイル内の要素。|  
  
## <a name="remarks"></a>コメント  
 通常、.vsct ファイルに含まれる 3 つ`GuidSymbol`内の要素の`Symbols`セクションで、パッケージ自体の 1 つ、(メニューのグループ、および、パッケージが利用できるようにするコマンドのコレクション)、コマンド セットの 1 つおよび提供されるビットマップの 1 つボタンおよびその他のビジュアル コンポーネントのアイコン。 各`IDSymbol`内の要素を指定した`GuidSymbol`要素は、一意でなければなりません`value`です。ただし、`IDSymbol`別の親を持っていれば、パッケージで同じ値を持つ要素が存在できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)