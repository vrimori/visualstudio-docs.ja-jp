---
title: GuidSymbol 要素 |Microsoft Docs
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
ms.openlocfilehash: 16e7a1b84a6baa26b69545b3fa55e4434e5998f3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500070"
---
# <a name="guidsymbol-element"></a>GuidSymbol 要素
`GuidSymbol`要素には、メニューのグループ、またはコマンドを表す GUID:ID のペアの GUID が含まれています。 ID に由来する`IDSymbol`内の要素、`GuidSymbol`要素。 `GuidSymbol`要素には、`name`属性に含まれていると、GUID のフレンドリ名を提供する、`value`属性。  
  
## <a name="syntax"></a>構文  
  
```xml  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|必須。 GUID 記号の名前です。|  
|値|必須。 GUID 記号の GUID です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[IDSymbol 要素](../extensibility/idsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID のペアの ID が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Symbols 要素](../extensibility/symbols-element.md)|グループ`GuidSymbol`内の要素を *.vsct*ファイル。|  
  
## <a name="remarks"></a>Remarks  
 通常、 *.vsct*ファイルには、3 つが含まれている`GuidSymbol`内の要素の`Symbols`セクションで、パッケージ自体の 1 つ、(メニューのコレクション グループ]、[コマンドのパッケージが使用できるようにする) は、コマンド セットの 1 つとビットマップのボタンおよびその他のビジュアル コンポーネント アイコンを提供する 1 つです。 すべて`IDSymbol`内の要素を指定した`GuidSymbol`要素は一意でなければなりません`value`します。ただし、`IDSymbol`別の親がある限り、パッケージに同じ値を持つ要素が存在できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)