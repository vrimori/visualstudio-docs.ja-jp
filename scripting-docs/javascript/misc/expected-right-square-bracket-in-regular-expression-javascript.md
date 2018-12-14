---
title: 正規表現の中に &#39;]&#39; が必要です (JavaScript) |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283718"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>正規表現の中に&#39;]&#39;が必要です (JavaScript)
正規表現の一致では、文字クラスを作成しようとしましたが、右角かっこが含まれていません。 個々 のリテラル文字の組み合わせは、角かっこ内に配置して文字クラスに組み立てられることができます。 文字クラスでは、含まれている任意の 1 文字と一致します。 たとえば、/[abc]"a"、"b"、文字のいずれかと一致する/または"c"です。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   正規表現に右角かっこを追加します。  
  
    > [!NOTE]
    >  1 つの角かっこと一致する場合は、円記号のエスケープ\\[によって特殊文字として解釈されないように -[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現構文 (JavaScript)](https://msdn.microsoft.com/library/1400241x)