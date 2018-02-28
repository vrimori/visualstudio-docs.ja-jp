---
title: "エンコードする URI に無効な文字が含まれています |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>エンコードする URI は無効な文字を含んでいます。
URI (Uniform Resource Identifier) として文字列をエンコードしようとしましたが、無効な文字が含まれています。 ほとんどの文字は、Uri に変換する文字列内では有効、一部の Unicode 文字のシーケンスは無効です。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   エンコードする文字列には、有効な Unicode シーケンスのみが含まれていることを確認します。 完全な URI は、コンポーネントと区切り文字のシーケンスで構成されます。 山かっこ内の名前は、のコンポーネントを表すおよび":"、「/」、「;」と"?"予約文字が区切り記号として使用します。 一般的な形式は次のとおりです。  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 関数](../../javascript/reference/encodeuricomponent-function-javascript.md)