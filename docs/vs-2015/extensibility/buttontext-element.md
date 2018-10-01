---
title: ButtonText 要素 |Microsoft Docs
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
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7cbf92a762fd3fce80e7f59e77c03c8cd81cc22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534382"
---
# <a name="buttontext-element"></a>ButtonText 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ButtonText 要素](https://docs.microsoft.com/visualstudio/extensibility/buttontext-element)します。  
  
このフィールドでは、さまざまなメニューに表示されるテキストを指定できます。 既定で、`ButtonText`要素は、メニュー コント ローラーに表示されます。 `ButtonText`他のテキスト フィールドが空白の場合に要素が既定値にもになります。 `ButtonText`場合でも、他のテキスト フィールドが指定された要素を空にすることはできません。  
  
## <a name="syntax"></a>構文  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ 要素](../extensibility/strings-element.md)|など、テキスト要素をグループ化`ButtonText`と`CommandName`します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値、`ButtonText`要素がメニュー項目、combos、およびテキストが表示されている他のユーザー インターフェイス (UI) 要素に表示されるテキストを提供します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

