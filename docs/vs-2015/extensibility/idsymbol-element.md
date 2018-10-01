---
title: IDSymbol 要素 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3ab239c85fbf3e9ebc83825750b78a1e6fdbf7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535129"
---
# <a name="idsymbol-element"></a>IDSymbol 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDSymbol 要素](https://docs.microsoft.com/visualstudio/extensibility/idsymbol-element)します。  
  
`IDSymbol`要素には、メニューのグループ、またはコマンドを表す GUID:ID のペアの ID が含まれています。 GUID は、親から`GuidSymbol`要素。 `IDSymbol`要素には、`name`属性に含まれていると、ID のフレンドリ名を提供する、`value`属性。  
  
## <a name="syntax"></a>構文  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|必須。 ID のシンボルの名前です。|  
|値|必須。 ID のシンボルの数値の ID の値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[GuidSymbol 要素](../extensibility/guidsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID のペアの GUID が含まれています。 複数の `IDSymbol` 要素をグループ化します。|  
  
## <a name="remarks"></a>Remarks  
 すべて`IDSymbol`内の要素を指定した`GuidSymbol`要素は一意でなければなりません`value`します。 ただし、`IDSymbol`別の親がある限り、パッケージに同じ値を持つ要素が存在できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

