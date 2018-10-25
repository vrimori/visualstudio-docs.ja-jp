---
title: エンコードする URI に無効な文字が含まれています |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832175"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>エンコードする URI は無効な文字を含んでいます。
URI (Uniform Resource Identifier) として文字列をエンコードしようとしましたが、無効な文字が含まれています。 ほとんどの文字は Uri に変換する文字列内で有効ですが、一部の Unicode 文字のシーケンスはできません。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   エンコードする文字列には、有効な Unicode シーケンスだけが含まれていることを確認します。 完全な URI は、コンポーネントや区切り文字のシーケンスで構成されます。 山かっこ内の名前は、コンポーネントを表す、":"、「/」、「;」と"?"予約文字が区切り記号として使用します。 一般的な形式です。  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 関数](../../javascript/reference/encodeuricomponent-function-javascript.md)