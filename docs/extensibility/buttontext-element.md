---
title: "ButtonText 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c9f2374af403c37f18d1aa91700e51bd038a71c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="buttontext-element"></a>ButtonText 要素
このフィールドでは、さまざまなメニューに表示されるテキストを指定できます。 既定では、`ButtonText`要素は、メニュー コント ローラーに表示されます。 `ButtonText`他のテキスト フィールドが空白の場合に要素が既定値にもになります。 `ButtonText`場合でも、他のテキスト フィールドが指定された要素を空白にすることはできません。  
  
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
|[ 要素](../extensibility/strings-element.md)|などのテキスト要素をグループ化`ButtonText`と`CommandName`です。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値、`ButtonText`要素は、メニュー項目、コンボ、および表示のテキストがあるその他のユーザー インターフェイス (UI) 要素について表示されるテキストを提供します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)