---
title: デコードする URI は有効なはエンコードされていません |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633332"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>デコードする URI は正しくエンコードされていません。
形式の正しくない URI (Uniform Resource Identifier) をデコードしようとしました。 Uri がある特殊な構文です。URI で使用できるように、ほとんどの英数字以外の文字をエンコードする必要があります。 使用することができます、`encodeURI`と`encodeURIComponent`通常から URI を作成するメソッド[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]文字列。  
  
 完全な URI は、コンポーネントと区切り文字のシーケンスで構成されます。 一般的な形式は次のとおりです。  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 山かっこ内の名前は、のコンポーネントを表すおよび":"、「/」、「;」と"?"予約文字が区切り記号として使用します。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   有効な Uri だけをデコードしようとしていることを確認します。 通常をデコードすることはできません[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]文字列、無効な文字を含めるように可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)