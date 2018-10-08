---
title: GuidSymbol 要素 |Microsoft Docs
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
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e6e5bab37e9a0b9f0ffdf03778532d9657539c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539410"
---
# <a name="guidsymbol-element"></a>GuidSymbol 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[GuidSymbol 要素](https://docs.microsoft.com/visualstudio/extensibility/guidsymbol-element)します。  
  
`GuidSymbol`要素には、メニューのグループ、またはコマンドを表す GUID:ID のペアの GUID が含まれています。 ID に由来する`IDSymbol`内の要素、`GuidSymbol`要素。 `GuidSymbol`要素には、`name`属性に含まれていると、GUID のフレンドリ名を提供する、`value`属性。  
  
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
|値|必須。 GUID 記号の GUID です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[IDSymbol 要素](../extensibility/idsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID のペアの ID が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Symbols 要素](../extensibility/symbols-element.md)|グループ`GuidSymbol`.vsct ファイル内の要素。|  
  
## <a name="remarks"></a>Remarks  
 通常、.vsct ファイルを含む 3 つ`GuidSymbol`内の要素の`Symbols`セクション、パッケージ自体の 1 つ、コマンド セット (メニューのグループ、および、パッケージが利用できるようにするコマンドのコレクション) の 1 つおよび 1 つのビットマップを提供します。ボタンやその他のビジュアル コンポーネントのアイコン。 すべて`IDSymbol`内の要素を指定した`GuidSymbol`要素は一意でなければなりません`value`します。ただし、`IDSymbol`別の親がある限り、パッケージに同じ値を持つ要素が存在できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

