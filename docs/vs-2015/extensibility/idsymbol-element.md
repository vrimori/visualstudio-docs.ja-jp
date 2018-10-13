---
title: IDSymbol 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 3b4876144093d5e937a194095af1b128dc3efabd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253046"
---
# <a name="idsymbol-element"></a>IDSymbol 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

